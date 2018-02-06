# Update Groups in AWS Resource Groups<a name="updating-resource-groups"></a>

To update a resource group in Resource Groups, you can edit the query and tags that are the basis of your group\. You can add and remove resources from your group only by applying changes to the query or tags; you cannot select specific resources to add to or remove from your group\. The best way to add or remove a specific resource from a group is to edit the resource's tags, then verify that your resource group tag query either includes or omits the tag depending on whether you want the resource in your group\.

In the AWS CLI, you update groups in two commands; `update-group`, which you run to update a group's description, and `update-group-query`, which you run to update the resource query and tags that determine the group's member resources\.

**To update a query and group in Resource Groups by using the AWS Management Console**

1. Open Resource Groups from the AWS Systems Manager console, or from the top left of the AWS Management Console\.

1. Under **Saved resource groups** in the navigation pane, choose an existing group, and then choose **Edit**\.

1. On the **Edit group** page, in the **Grouping criteria** area, add or remove resource types as desired\. To remove a resource type, choose **X** on the resource type's label\. Choose **View group resources** to see how the changes affect your group's resource members\. In this walkthrough, we add the resource type **AWS::RDS::DBInstance** to the query\.  
![\[Group query\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-update-group-query.png)

1. Edit tags, if necessary\. In this example, we filter for resources that have a tag key of **Stage**, and add a tag value of **Test**\. The tag value is optional, but narrows the results of the query further\.  
![\[Group tags\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-update-tags.png)

1. In the **Additional information** area, you can edit the group description\. You cannot edit an existing group's name\.  
![\[Group name and description\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-groupname-desc.png)

1. In the **Group tags** area, add or remove tags as desired\. Group tags are metadata about your resource group; they do not affect member resources\. To change the resources that are returned by the resource group's query, edit tags in the **Grouping criteria** area\.

1. Choose **View query results** to return the updated list of EC2 instances, S3 buckets, and Amazon RDS database instances in your account that match the specified tag keys\. If you do not see resources in the list that you expect, be sure that the resources are tagged with tags that you specified in the **Grouping criteria** area\.

1. When you are finished, choose **Save changes**\.

**To update a group in Resource Groups by using the AWS CLI**

In the AWS CLI, you update a group's query and update a resource group's description by using two different commands\. You cannot change the name of a group by using the AWS CLI\.

1. If you do not want to change the description of your group, skip this step and go on to the next\. In an AWS CLI session, type the following, and then press **Enter**, replacing the values for group name and description with your own\.

   ```
   aws resource-groups update-group --group-name resource-group-name --description "description_text"
   ```

   The following command is an example\.

   ```
   aws resource-groups update-group --group-name my-resource-group --description "EC2 instances, S3 buckets, and RDS DBs that we are using for the test stage."
   ```

   The command returns a full, updated description of the group\.

1. To update the query and tags of a group, type the following command, and then press **Enter**, replacing the values for group name, resource types, tag keys, and tag values with your own\.

   ```
   aws resource-groups update-group-query --name resource-group-name --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"resource_type1\",\"resource_type2"],\"TagFilters\":[{\"Key\":\"Key1\",\"Values\":[\"Value1\",\"Value2\"]},{\"Key\":\"Key2\",\"Values\":[\"Value1\",\"Value2\"]}]}"}'
   ```

   The following command is an example\.

   ```
   aws resource-groups update-group-query --name my-resource-group --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\",\"AWS::S3::Bucket\",\"AWS::RDS::DBInstance\"],\"TagFilters\":[{\"Key\":\"Stage\",\"Values\":[\"Test\"]}]}"}'
   ```

   The command returns the updated query as a result\.