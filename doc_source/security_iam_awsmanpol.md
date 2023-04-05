# AWS managed policies for AWS Resource Groups<a name="security_iam_awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the `ViewOnlyAccess` AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

**AWS\-managed policies for Resource Groups**
+ [ResourceGroupsServiceRolePolicy](#security-iam-awsmanpol-ResourceGroupsServiceRolePolicy)

## AWS managed policy: ResourceGroupsServiceRolePolicy<a name="security-iam-awsmanpol-ResourceGroupsServiceRolePolicy"></a>

You can't attach `ResourceGroupsServiceRolePolicy` to any IAM entities yourself\. This policy can be attached only to a service\-linked role that allows Resource Groups to perform actions on your behalf\. For more information, see [Using service\-linked roles for Resource Groups](security_iam_service-linked-roles.md)\.

This policy grants the permissions required for Resource Groups to retrieve information about the resources in your resource groups and any AWS CloudFormation stacks that that those resources belong to\. This lets Resource Groups generate CloudWatch Events for the group lifecycle events feature\. 

To see the latest version of this AWS managed policy, see `[ResourceGroupsServiceRolePolicy](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsServiceRolePolicy)` in the IAM console\.

## Resource Groups updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for Resource Groups since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the [Resource Groups Document history](doc-history.md) page\.


| Change | Description | Date | 
| --- | --- | --- | 
| New policy – [ResourceGroupsServiceRolePolicy](#security-iam-awsmanpol-ResourceGroupsServiceRolePolicy.title) | Resource Groups added a new policy to support its service\-linked role\. | November 17, 2022 | 
|  Resource Groups started tracking changes  |  Resource Groups started tracking changes for its AWS managed policies\.  | November 17, 2022 | 