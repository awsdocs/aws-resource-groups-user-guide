# AWS Resource Groups and Tagging Reference<a name="reference"></a>

Use the topics in this section to find reference information for various aspects of AWS Resource Groups\.

## Service quotas for Resource Groups<a name="arg-reference-quotas"></a>

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/reference.html)

**Note**  
You can request changes to quotas marked as adjustable by using the [AWS Resource Groups page in the Service Quotas console](https://console.aws.amazon.com/servicequotas/home/services/resource-groups/quotas)\.

## Service quotas for Tagging \(Tag Editor and Resource Groups Tagging API\)<a name="taged-reference-quotas"></a>


| Name | Default | 
| --- | --- | 
|  Tags attached per resource  |  50 user created tags \(AWS created tags don't count against this limit\)  | 
|  Tag key name  |  Minimum of 1, maximum 128 Unicode characters in UTF\-8\. Allowed characters include: letters, numbers, spaces, and the following characters: `_ . : / = + - @` Key names can't begin with `aws:` because that is reserved\.  Some AWS services have some additional character or length restrictions\. For details, see the documentation for the specific service\.   | 
|  Tag values  |  Minimum of 0, maximum of 256 Unicode characters in UTF\-8\. Allowed characters include: letters, numbers, spaces, and the following characters: `_ . : / = + - @`  Some AWS services have some additional character or length restrictions\. For details, see the documentation for the specific service\.   | 
|  Rate of calling the [GetResources](https://docs.aws.amazon.com/resourcegroupstagging/latest/APIReference/API_GetResources.html) API operation  |  Maximum of 15 calls per second  | 
|  Rate of calling the following API operations: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/reference.html)  |  Maximum of 5 calls per second  | 

**Note**  
These limits are currently not adjustable using the [Service Quotas console](https://console.aws.amazon.com/servicequotas/home/services/resource-groups/quotas)\. Contact AWS Support\.

## AWS managed policies available for use with AWS Resource Groups and Tag Editor<a name="arg-reference-managed-policies"></a>

[AWS\-managed IAM permission policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) enable you to grant pre\-configured permissions to the IAM users and roles in your account\. AWS managed policies are tested and adhere to best practice recommendations, so you can reliably use them in the scenarios for which they're define\. As new resource types are supported as members of resource groups, and as new resource types support tagging, AWS automically updates these policies to support them\. You don't need to do anything\.

The following table lists the AWS\-managed IAM permission policies available for you to use to grant permissions to AWS Resource Groups\.


****  

| Policy name and ARN | Description | 
| --- | --- | 
|  [AWSResourceGroupsReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess$jsonEditor) `arn:aws:iam::aws:policy/AWSResourceGroupsReadOnlyAccess`  | Grants read\-only access to the AWS Resource Groups management console\. It includes permission to view the details of a resource, including the list of attached tags\. This policy doesn't grant permission to make any changes to resource groups or tags\. | 
|  [ResourceGroupsandTagEditorReadOnlyAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess$jsonEditor) `arn:aws:iam::aws:policy/ResourceGroupsandTagEditorReadOnlyAccess`  | Grants read\-only access to the AWS Resource Groups management console, including the Tag Editor\. It includes permission to view the details of a resource, including its tags\. You can use the Tag Editor to view resources that match tag queries\. This policy doesn't grant permission to make any changes to resource groups or tags\. | 
|  [ResourceGroupsandTagEditorFullAccess](https://console.aws.amazon.com/iam/home#/policies/arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess$jsonEditor) `arn:aws:iam::aws:policy/ResourceGroupsandTagEditorFullAccess`  | Grants full administrative access to the AWS Resource Groups management console\. It includes permissions to view, create, and modify resource groups\. It also includes permissions to view, set, and modify tags for any resources that are supported by Tag Editor\. | 