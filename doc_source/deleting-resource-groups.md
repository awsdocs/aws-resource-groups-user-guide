# Delete Groups from AWS Resource Groups<a name="deleting-resource-groups"></a>

You can delete resource groups from AWS Resource Groups by using either the Resource Groups console or the AWS CLI\. Deleting a resource group does not delete the resources that are members of the group, or tags on member resources; it deletes only the group structure, and any group\-level tags\.

**To delete resource groups in the AWS Management Console**

1. In the AWS Systems Manager console navigation pane, or from the Resource Groups drop\-down menu on the AWS home page, choose **Saved Resource Groups**\.

1. Choose the resource group that you want to delete\.

1. On the group's detail page, choose **Delete**\.

1. When you are prompted to confirm the deletion, choose **Delete**\.

**To delete resource groups by using the AWS CLI**

1. Type the following command, replacing *resource\_group\_name* with the name of your group, and then press **Enter**\.

   ```
   aws resource-groups delete-group --group-name resource_group_name
   ```

1. When you are prompted to confirm the deletion, type `yes`, and then press **Enter**\.