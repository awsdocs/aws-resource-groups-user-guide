# Creating query\-based groups in AWS Resource Groups<a name="gettingstarted-query"></a>

**Topics**
+ [Types of resource group queries](#getting_started-query_types)
+ [Build a tag\-based query and create a group](#gettingstarted-query-tag-based)
+ [Create an AWS CloudFormation stack\-based group](#gettingstarted-query-stack-based)

## Types of resource group queries<a name="getting_started-query_types"></a>

In AWS Resource Groups, a *query* is the foundation of a query\-based group\. You can base a resource group on one of two types of queries\.

 **Tag\-based**   
Tag\-based queries include lists of resource types that are specified in the following format `AWS::service::resource`, and tags\. *Tags* are keys that help identify and sort your resources in your organization\. Optionally, tags include values for keys\.  
For a tag\-based query, you also specify the tags that are shared by the resources that you want to be members of the group\. For example, if you want to create a resource group that has all of the Amazon EC2 instances and Amazon S3 buckets that you are using to run the testing stage of an application, and you have instances and buckets that are tagged this way, choose the `AWS::EC2::Instance` and `AWS::S3::Bucket` resource types from the drop\-down list, and then specify the tag key **Stage**, with a tag value of **Test**\.  
The syntax of the `ResourceQuery` parameter of a tag\-based resource group contains the following elements:  
+  `Type` 

  This element indicates which kind of query defines this resource group\. To create a tag\-based resource group, specify the value `TAG_FILTERS_1_0`, as follows:

  ```
  "Type": "TAG_FILTERS_1_0"
  ```
+  `Query` 

   This element defines the actual query used to match against resources\. It contains a string representation of a JSON structure with the following elements:
  +  `ResourceTypeFilters` 

    This element limits the results to only those resource types that match the filter\. You can specify the following values:
    + `"AWS::AllSupported"` – to specify that the results can include resources of any type that match the query and that are currently supported by the Resource Groups service\.
    + `"AWS::service-id::resource-type` – a comma separated list of resource\-type specification strings with this format: , such as `"AWS::EC2::Instance"`\.
  +  `TagFilters` 

    This element specifies key/value string pairs that are compared to the tags attached to your resources\. Those with a tag key and value that match the filter are included in the group\. Each filter consists of these elements:
    + `"Key"` – a string with a key name\. Only resources that have tags with a matching key name match the filter and are members of the group\.
    + `"Values"` – a string with a comma separated list of values for the specified key\. Only resources with a matching tag key and a value that matches one in this list are members of the group\.
All of these JSON elements must be combined into a single\-line string representation of the JSON structure\. For example, consider a `Query` with the following example JSON structure\. This query is meant to match only Amazon EC2 instances that have a tag "Stage" with a value "Test"\.  

```
{
    "ResourceTypeFilters": [ "AWS::EC2::Instance" ],
    "TagFilters": [
        {
            "Key": "Stage",
            "Values": [ "Test" ]
        }
    ]
}
```
That JSON can be represented as the following single\-line string, and used as the value of the `Query` element\. Because the value of a JSON structure must be a double\-quoted string, you must escape any embedded double\-quote characters or forward slash characters by preceding each with a backslash as shown here:  

```
"Query":"{\"ResourceTypeFilters\":[\"AWS::AllSupported\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"
```
The complete `ResourceQuery` string is then represented as shown here, as a CLI command parameter:  

```
--resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::AllSupported\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"}'
```

  **AWS CloudFormation stack\-based**   
In an AWS CloudFormation stack\-based query, you choose an AWS CloudFormation stack in your account in the current region, and then choose resource types in the stack that you want to be in the group\. You can base your query on only one AWS CloudFormation stack\.   
An AWS CloudFormation stack can contain other AWS CloudFormation "child" stacks\. However, a resource group based on a "parent" stack doesn't get all of the child stacks' resources as group members\. Resource groups adds the child stacks to the parent stack's resource group as single group members and doesn't expand them\.
Resource Groups supports queries based on AWS CloudFormation stacks that have one of the following statuses\.  
+ `CREATE_COMPLETE`
+ `CREATE_IN_PROGRESS`
+ `DELETE_FAILED`
+ `DELETE_IN_PROGRESS`
+ `REVIEW_IN_PROGRESS`
Only resources that are directly created as part of the stack in the query are included in the resource group\. Resources created later by members of the AWS CloudFormation stack do not become members of the group\. For example, if an auto\-scaling group is created by AWS CloudFormation as part of the stack, then that auto\-scaling group ***is*** a member of the group\. However, an Amazon EC2 instance created by that auto\-scaling group as part of its operation ***is not*** a member of the AWS CloudFormation stack\-based resource group\. 
If you create a group based on an AWS CloudFormation stack, and the stack's status changes to one that is no longer supported as a basis for a group query, such as `DELETE_COMPLETE`, the resource group still exists, but it has no member resources\.

After you create a resource group, you can perform tasks on the resources in the group\.

The syntax of the `ResourceQuery` parameter of a CloudFormation stack\-based resource group contains the following elements:
+  `Type` 

  This element indicates which kind of query defines this resource group\. 

  To create a AWS CloudFormation stack\-based resource group, specify the value `CLOUDFORMATION_STACK_1_0`, as follows:

  ```
  "Type": "CLOUDFORMATION_STACK_1_0"
  ```
+  `Query` 

   This element defines the actual query used to match against resources\. It contains a string representation of a JSON structure with the following elements:
  +  `ResourceTypeFilters` 

    This element limits the results to only those resource types that match the filter\. You can specify the following values:
    + `"AWS::AllSupported"` – to specify that the results can include resources of any type that match the query\.
    + `"AWS::service-id::resource-type` – a comma separated list of resource\-type specification strings with this format: , such as `"AWS::EC2::Instance"`\.
  +  `StackIdentifier` 

    This element specifies the Amazon Resource Name \(ARN\) of the AWS CloudFormation stack whose resources you want to include in the group\.

All of these JSON elements must be combined into a single\-line string representation of the JSON structure\. For example, consider a `Query` with the following example JSON structure\. This query is meant to match only Amazon S3 buckets that are part of the specified AWS CloudFormation stack\.

```
{
    "ResourceTypeFilters": [ "AWS::S3::Bucket" ],
    "StackIdentifier": "arn:aws:cloudformation:us-west-2:123456789012:stack/MyCloudFormationStackName/fb0d5000-aba8-00e8-aa9e-50d5cEXAMPLE"
}
```

That JSON can be represented as the following single\-line string, and used as the value of the `Query` element\. Because the value of a JSON structure must be a double\-quoted string, you must escape any embedded double\-quote characters or forward slash characters by preceding each with a backslash as shown here:

```
"Query":"{\"ResourceTypeFilters\":[\"AWS::S3::Bucket\"],\"StackIdentifier\":\"arn:aws:cloudformation:us-west-2:123456789012:stack\/MyCloudFormationStackName\/fb0d5000-aba8-00e8-aa9e-50d5cEXAMPLE\"
```

The complete `ResourceQuery` string is then represented as shown here, as a CLI command parameter:

```
--resource-query '{"Type":"CLOUDFORMATION_STACK_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::S3::Bucket\"],\"StackIdentifier\":\"arn:aws:cloudformation:us-west-2:123456789012:stack\/MyCloudFormationStackName\/fb0d5000-aba8-00e8-aa9e-50d5cEXAMPLE\"}'
```

## Build a tag\-based query and create a group<a name="gettingstarted-query-tag-based"></a>

The following procedures show you how to build a tag\-based query and use it to create a resource group\.

------
#### [ Console ]

1. Sign in to the [AWS Resource Groups console](https://console.aws.amazon.com/resource-groups)\.

1. In the navigation pane, choose **[Create Resource Group](https://console.aws.amazon.com/resource-groups/groups/new)**\.

1. On the **Create query\-based group** page, under **Group type**, choose the **Tag based** group type\.

1. Under **Grouping criteria**, choose the resource types that you want to be in your resource group\. You can have a maximum of 20 resource types in a query\. For this walkthrough, choose **AWS::EC2::Instance** and **AWS::S3::Bucket**\. 

1. Still under **Grouping criteria**, for **Tags**, specify a tag key, or a tag key and value pair, to limit the matching resources to include only those that are tagged with your specified values\. Choose **Add** or press **Enter** when you've finished your tag\. In this example, filter for resources that have a tag key of **Stage**\. The tag value is optional, but narrows the results of the query further\. You can add multiple values for a tag key by adding an `OR` operator between tag values\. To add more tags, choose **Add**\. Queries assign an `AND` operator to tags, so any resource that matches the specified resource types and all specified tags is returned by the query\.

1. Still under **Grouping criteria**, choose **Preview group resources** to return the list of EC2 instances and S3 buckets in your account that match the specified tag key or keys\.

1. After you have the results that you want, create a group based on this query\.

   1. Under **Group details**, for **Group name**, type a name for your resource group\.

      A resource group name can have a maximum of 128 characters, including letters, numbers, hyphens, periods, and underscores\. The name cannot start with `AWS` or `aws`\. These are reserved\. A resource group name must be unique in the current Region in your account\.

   1. \(Optional\) In **Group description**, enter a description of your group\.

   1. \(Optional\) In **Group tags**, add tag key and value pairs that apply only to the resource group, not the member resources in the group\.

      Group tags are useful if you plan to make this group a member of a larger group\. Because specifying at least a tag key is required to create a group, be sure to add at least a tag key in **Group tags** to groups that you plan to nest into larger groups\.

1. When you're finished, choose **Create group**\.

------
#### [ AWS CLI & AWS SDKs ]

A tag\-based group is based on a query of type `TAG_FILTERS_1_0`\.

1. In an AWS CLI session, type the following, and then press **Enter**, replacing the values for group name, description, resource types, tag keys, and tag values with your own\. Descriptions can have a maximum of 512 characters, including letters, numbers, hyphens, underscores, punctuation, and spaces\. You can have a maximum of 20 resource types in a query\. A resource group name can have a maximum of 128 characters, including letters, numbers, hyphens, periods, and underscores\. The name cannot start with `AWS` or `aws`\. These are reserved\. A resource group name must be unique in your account\.

   At least one value for `ResourceTypeFilters` is required\. To specify all resource types, use `AWS::AllSupported` as the `ResourceTypeFilters` value\.

   ```
   $ aws resource-groups create-group \
       --name resource-group-name \
       --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"resource_type1\",\"resource_type2\"],\"TagFilters\":[{\"Key\":\"Key1\",\"Values\":[\"Value1\",\"Value2\"]},{\"Key\":\"Key2\",\"Values\":[\"Value1\",\"Value2\"]}]}"}'
   ```

   The following command is an example\.

   ```
   $ aws resource-groups create-group \
       --name my-resource-group \
       --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"}'
   ```

   The following command is an example that includes all supported resource types\.

   ```
   $ aws resource-groups create-group \
       --name my-resource-group \
       --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::AllSupported\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"}'
   ```

1. The following are returned in the response to the command\.
   + A full description of the group you have created\.
   + The resource query that you used to create the group\.
   + The tags that are associated with the group\.

------

## Create an AWS CloudFormation stack\-based group<a name="gettingstarted-query-stack-based"></a>

The following procedures show you how to build a stack\-based query and use it to create a resource group\.

------
#### [ Console ]

1. Sign in to the [AWS Resource Groups console](https://console.aws.amazon.com/resource-groups)\.

1. In the navigation pane, choose **[Create Resource Group](https://console.aws.amazon.com/resource-groups/groups/new)**\.

1. On **Create query\-based group**, under **Group type**, choose the **CloudFormation stack based** group type\.

1. Choose the stack that you want to be the basis of your group\. A resource group can be based on only one stack\. To filter the list of stacks, start typing the name of the stack\. Only stacks with supported statuses appear in the list\.

1. Choose resource types in the stack that you want to include in the group\. For this walkthrough, keep the default, **All supported resource types**\. For more information about which resource types are supported and can be in the group, see [Resource types you can use with AWS Resource Groups and Tag Editor](supported-resources.md)\.

1. Choose **View group resources** to return the list of resources in the AWS CloudFormation stack that match your selected resource types\.

1. After you have the results that you want, create a group based on this query\.

   1. Under **Group details**, for **Group name**, type a name for your resource group\.

      A resource group name can have a maximum of 128 characters, including letters, numbers, hyphens, periods, and underscores\. The name cannot start with `AWS` or `aws`\. These are reserved\. A resource group name must be unique in the current Region in your account\.

   1. \(Optional\) In **Group description**, enter a description of your group\.

   1. \(Optional\) In **Group tags**, add tag key and value pairs that apply only to the resource group, not the member resources in the group\.

      Group tags are useful if you plan to make this group a member of a larger group\. Because specifying at least a tag key is required to create a group, be sure to add at least a tag key in **Group tags** to groups that you plan to nest into larger groups\.

1. When you're finished, choose **Create group**\.

------
#### [ AWS CLI & AWS SDKs ]

An AWS CloudFormation stack\-based group is based on a query of type `CLOUDFORMATION_STACK_1_0`\.

1. Run the following command, replacing the values for group name, description, stack identifier, and resource types with your own\. Descriptions can have a maximum of 512 characters, including letters, numbers, hyphens, underscores, punctuation, and spaces\.

   If you do not specify resource types, Resource Groups includes all supported resource types in the stack\. You can have a maximum of 20 resource types in a query\. A resource group name can have a maximum of 128 characters, including letters, numbers, hyphens, periods, and underscores\. The name cannot start with `AWS` or `aws`\. These are reserved\. A resource group name must be unique in your account\.

   The *stack\_identifier* is the stack ARN, as shown in the example command\.

   ```
   $ aws resource-groups create-group \
       --name group_name \
       --description "description" \
       --resource-query '{"Type":"CLOUDFORMATION_STACK_1_0","Query":"{\"StackIdentifier\":\"stack_identifier\",\"ResourceTypeFilters\":[\"resource_type1\",\"resource_type2\"]}"}'
   ```

   The following command is an example\.

   ```
   $ aws resource-groups create-group \
       --name My-CFN-stack-group \
       --description "My first CloudFormation stack-based group" \
       --resource-query '{"Type":"CLOUDFORMATION_STACK_1_0","Query":"{\"StackIdentifier\":\"arn:aws:cloudformation:us-west-2:123456789012:stack\/AWStestuseraccount\/fb0d5000-aba8-00e8-aa9e-50d5cEXAMPLE\",\"ResourceTypeFilters\":[\"AWS::EC2::Instance\",\"AWS::S3::Bucket\"]}"}'
   ```

1. The following are returned in the response to the command\.
   + A full description of the group you have created\.
   + The resource query that you used to create the group\.

------