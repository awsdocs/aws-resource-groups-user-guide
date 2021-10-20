# AWS Resource Groups Reference<a name="reference"></a>

Use the topics in this section to find reference information for various aspects of AWS Resource Groups\.

## Service quotas for Resource Groups<a name="arg-reference-quotas"></a>

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/reference.html)

**Note**  
You can request changes to quotas marked as adjustable by using the [AWS Resource Groups page in the Service Quotas console](https://console.aws.amazon.com/servicequotas/home/services/resource-groups/quotas)\.

## AWS managed policies available for use with AWS Resource Groups<a name="arg-reference-managed-policies"></a>

[AWS\-managed IAM permission policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) enable you to grant pre\-configured permissions to the IAM users and roles in your account\. AWS managed policies are tested and adhere to best practice recommendations, so you can reliably use them in the scenarios for which they're define\. As new resource types are supported as members of resource groups, and as new resource types support tagging, AWS automically updates these policies to support them\. You don't need to do anything\.

The following table lists the AWS\-managed IAM permission policies available for you to use to grant permissions to AWS Resource Groups\.


****  

| Policy name | Description | ARN | 
| --- | --- | --- | 
| [AWSResourceGroupsReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess$jsonEditor) | Grants read\-only access to the AWS Resource Groups management console\. It includes permission to view the details of a resource, including the list of attached tags\. This policy doesn't grant permission to make any changes to resource groups or tags\. | arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess | 
| [ResourceGroupsandTagEditorReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess$jsonEditor) | Grants read\-only access to the AWS Resource Groups management console, including the Tag Editor\. It includes permission to view the details of a resource, including its tags\. You can use the Tag Editor to view resources that match tag queries\. This policy doesn't grant permission to make any changes to resource groups or tags\. | arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess | 
| [ResourceGroupsandTagEditorFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess$jsonEditor) | Grants full administrative access to the AWS Resource Groups management console\. It includes permissions to view, create, and modify resource groups\. It also includes permissions to view, set, and modify tags for any resources that are supported by Tag Editor\. | arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess | 