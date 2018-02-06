# Build Queries and Groups in AWS Resource Groups<a name="gettingstarted-query"></a>

In AWS Resource Groups, a *query* is the foundation of a group\. To build a query, you choose the types of resources that you want to be part of the group, and then specify the tags that are shared by the resources that you want to be members of the group\. For example, if you want to create a resource group that has all of the Amazon EC2 instances and Amazon S3 buckets that you are using to run the testing stage of an application, and you have instances and buckets that are tagged this way, you choose the `AWS::EC2::Instance` and `AWS::S3::Bucket` resource types from the drop\-down list, and then specify the tag key **Stage**, with a tag value of **Test**\.

In the AWS CLI, you build a query and create your resource group in the same command\. The AWS CLI command shown in this topic creates a group\.

**To build a query and create a group in Resource Groups by using the AWS Management Console**

1. Open Resource Groups from the AWS Systems Manager console, or from the top left of the AWS Management Console\.

1. Choose **Create a resource group**\.  
![\[Create a resource group page.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-aramis-home.png)

1. On the **Create a resource group** page, choose the resource types that you want to be in your resource group\. For the purposes of this walkthrough, we are choosing **AWS::EC2::Instance** and **AWS::S3::Bucket**\.  
![\[Create a resource group page, EC2 instance and S3 bucket resource types selected.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-instancebucket-selected.png)

1. In the tag string boxes, specify a tag key, or a tag key and value pair, to limit the EC2 instances and S3 buckets in your account to only those that are tagged with your specified values\. Choose **\+** or press **Enter** when you've finished your tag\. In this example, we filter for resources that have a tag key of **Stage**\. The tag value is optional, but narrows the results of the query further\. To add more tags, choose **\+**\. Queries assign an `AND` operator to tags, so any resource that matches the specified resource types and all specified tags is returned by the query\.  
![\[Query with tag key specified.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-query-tags.png)

1. Choose **View group resources** to return the list of EC2 instances and S3 buckets in your account that match the specified tag key or keys\.

1. To create a resource group based on your query, specify a name, and optionally, add a description\.

   1. In the **Group name** box, type a name for your resource group\.

      A resource group name can have a maximum of 127 characters, including letters, numbers, hyphens, dots, and underscores\. The name cannot start with `AWS` or `aws`; these are reserved\. A resource group name must be unique within the current region in your account\.

   1. Optionally, in the **Group description** box, type a description of your group\.

   1. Optionally, in the **Group tags** area, you can add tag key and value pairs that apply only to the resource group, not the member resources in the group\.

1. When you are finished, choose **Create group**\.

**To create a group in Resource Groups by using the AWS CLI**

In an AWS CLI command, you build a query and create a resource group based on the query in a single command\.

1. In an AWS CLI session, type the following, and then press **Enter**, replacing the values for group name, resource types, tag keys, and tag values with your own\. A resource group name can have a maximum of 127 characters, including letters, numbers, hyphens, dots, and underscores\. The name cannot start with `AWS` or `aws`; these are reserved\. A resource group name must be unique within your account\.

   ```
   aws resource-groups create-group --name resource-group-name --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"resource_type1\",\"resource_type2"],\"TagFilters\":[{\"Key\":\"Key1\",\"Values\":[\"Value1\",\"Value2\"]},{\"Key\":\"Key2\",\"Values\":[\"Value1\",\"Value2\"]}]}"}'
   ```

   The following command is an example\.

   ```
   aws resource-groups create-group --name my-resource-group --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"}'
   ```

1. The following are returned in the response to the command\.

   + A full description of the group you have created

   + The resource query that you used to create the group

   + The tags that are associated with the group