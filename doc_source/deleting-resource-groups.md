# Delete groups from AWS Resource Groups<a name="deleting-resource-groups"></a>

You can use the [AWS Resource Groups console](https://console.aws.amazon.com/resource-groups) or the AWS CLI to delete resource groups from AWS Resource Groups\. Deleting a resource group does not delete the resources that are members of the group or tags on member resources\. It deletes only the group structure and any group\-level tags\.

------
#### [ Console ]

**To delete resource groups**

1. Sign in to the [AWS Resource Groups console](https://console.aws.amazon.com/resource-groups)\.

1. Choose the name of the resource group that you want to delete\.

1. On the group's detail page, choose **Delete**\.

1. When you are prompted to confirm the deletion, choose **Delete**\.

------
#### [ AWS CLI & AWS SDKs ]

**To delete resource groups**

1. Run the following command, replacing *resource\_group\_name* with the name of your group\.

   ```
   $ aws resource-groups delete-group \
       --group-name resource_group_name
   ```

1. When you are prompted to confirm the deletion, type `yes`, and then press **Enter**\.

------