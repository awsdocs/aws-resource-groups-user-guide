# Using service\-linked roles for Resource Groups<a name="security_iam_service-linked-roles"></a>

AWS Resource Groups uses AWS Identity and Access Management \(IAM\)[ service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to Resource Groups\. Service\-linked roles are predefined by Resource Groups and include all the permissions that the service requires to call other AWS services on your behalf\. 

A service\-linked role makes setting up Resource Groups easier because you don’t have to manually add the necessary permissions\. Resource Groups defines the permissions of its service\-linked roles and sets trust policies on each that ensures that only the Resource Groups service can assume its roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy can't be attached to any other IAM entity\.

For information about other services that support service\-linked roles, see [AWS services that work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) and look for the services that have **Yes** in the **Service\-linked roles** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-linked role permissions for Resource Groups<a name="service-linked-role-permissions"></a>

Resource Groups uses the following service\-linked role to support group lifecycle events\. Choose the link on the role name to view the role in the IAM console after you create it\.
+ `[AWSServiceRoleForResourceGroups](https://console.aws.amazon.com/iamv2/home#/roles/details/AWSServiceRoleForResourceGroups)`

 Resource Groups uses the permissions in this role to query the AWS services that own your resources to help resolve group membership and to keep the group up\-to\-date\. It allows Resource Groups to emit service\-related events to the Amazon EventBridge service\.

The `AWSServiceRoleForResourceGroups` service\-linked role trusts ***only*** the following service to assume the role:
+ `resourcegroups.amazonaws.com`

The permissions attached to the role come from the following AWS managed policy\. Choose the link on the policy name to view the policy in the IAM console\.
+ `AWS managed policies for AWS Resource Groups`

## Creating the service\-linked role for Resource Groups<a name="create-service-linked-role"></a>

**Important**  
This service\-linked role can appear in your account if you complete an action in another service that requires the features supported by this role\. For more information, see [A new role appeared in my AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_roles.html#troubleshoot_roles_new-role-appeared)\.

To create the service\-linked role, [turn on the group lifecycle events feature](monitor-groups-turn-on.md)\.

## Editing a service\-linked role for Resource Groups<a name="edit-service-linked-role"></a>

Resource Groups doesn't allow you to edit the AWSServiceRoleForResourceGroups service\-linked role\. After you create a service\-linked role, you can't change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting a service\-linked role for Resource Groups<a name="delete-service-linked-role"></a>

You can delete the service\-linked role only after you turn off the group lifecycle events feature\. 

**Important**  
AWS prevents you from removing the service\-linked role until you first [turn off the group lifecycle events feature](monitor-groups-turn-off.md) that created it\.
We recommend that you do not delete the service\-linked role as long as you have any resource groups in your AWS account\. The Resource Groups service can't interact with other AWS services to manage your groups if you delete this role\.

### Manually delete the service\-linked role<a name="slr-manual-delete"></a>

Use the IAM console, the AWS CLI, or the AWS API to delete the AWSServiceRoleForResourceGroups service\-linked role\. For more information, see [Deleting a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.

------
#### [ Console ]

**To delete the Resource Groups service\-linked role**

1. Open the [IAM console to the Roles page](https://console.aws.amazon.com/iam/home#/roles)\.

1. Find the role named AWSServiceRoleForResourceGroups, and select the check box beside it\.

1. Choose **Delete**\.

1. Confirm your intent to delete the role by entering the role's name in the box, and then choose **Delete**\.

The role disappears from your list of roles in the IAM console\.

------
#### [ AWS CLI ]

**To delete the Resource Groups service\-linked role**  
To delete the role, enter the following command with the parameters exactly as shown\. Do not replace any of the values\.

```
$ aws iam delete-service-linked-role \
    --role-name AWSServiceRoleForResourceGroups
{
    "DeletionTaskId": "task/aws-service-role/resource-groups.amazonaws.com/AWSServiceRoleForResourceGroups/34e58943-e9a5-4220-9856-fc565EXAMPLE"
}
```

The command returns a task ID\. The actual role deletion occurs asynchronously\. You can check the status of the role deletion by passing the provided task identifier to the following AWS CLI command\.

```
$ aws iam get-service-linked-role-deletion-status \
    --deletion-task-id "task/aws-service-role/resource-groups.amazonaws.com/AWSServiceRoleForResourceGroups/34e58943-e9a5-4220-9856-fc565EXAMPLE"
{
    "Status": "SUCCEEDED"
}
```

------

## Supported Regions for Resource Groups service\-linked roles<a name="slr-regions"></a>

Resource Groups supports using service\-linked roles in all of the AWS Regions where the service is available\. For more information, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html)\.