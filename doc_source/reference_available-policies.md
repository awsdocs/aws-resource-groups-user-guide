# AWS Resource Groups Reference<a name="reference_available-policies"></a>

Use the topics in this section to find reference information for various aspects of AWS Resource Groups\.

## AWS managed policies available for use with AWS Resource Groups<a name="ref-managed-policies"></a>

[AWS\-managed IAM permission policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) enable you to grant pre\-configured permissions to the IAM users and roles in your account\. AWS managed policies are tested and adhere to best practice recommendations, so you can reliably use them in the scenarios for which they're define\. As new resource types are supported as members of resource groups, and as new resource types support tagging, AWS automically updates these policies to support them\. You don't need to do anything\.

The following table lists the AWS\-managed IAM permission policies available for you to use to grant permissions to AWS Resource Groups\.


****  

| Policy name | Description | ARN | 
| --- | --- | --- | 
| [AWSResourceGroupsReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess) | Grants read\-only access to the AWS Resource Groups management console\. It includes permission to view the details of a resource, including the list of attached tags\. This policy doesn't grant permission to make any changes to resource groups or tags\. | arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess | 
| [ResourceGroupsandTagEditorReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess) | Grants read\-only access to the AWS Resource Groups management console, including the Tag Editor\. It includes permission to view the details of a resource, including its tags\. You can use the Tag Editor to view resources that match tag queries\. This policy doesn't grant permission to make any changes to resource groups or tags\. | arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess | 
| [ResourceGroupsandTagEditorFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess) | Grants full administrative access to the AWS Resource Groups management console\. It includes permissions to view, create, and modify resource groups\. It also includes permissions to view, set, and modify tags for any resources that are supported by Tag Editor\. | arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess | 