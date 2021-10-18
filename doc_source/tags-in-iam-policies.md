# Using tags in IAM permission policies<a name="tags-in-iam-policies"></a>

[AWS Identity and Access Management \(IAM\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/) is the AWS service that you use to create and manage permission policies that determine who can access your AWS resources\. Every attempt to access an AWS service or read or write an AWS resource is access controlled by such an IAM policy\.

These policies allow you to provide granular access to your resources\. One of the features you can use to fine tune this access is the `Condition` element of the policy\. This element lets you specify the additional conditions that must match the request to determine if the request can proceed\. Among the things you can check with the `Condition` element are the tags that are attached to the user or role making the request and the tags attached to the resource that is the object of the request\.

## Tag\-related condition keys<a name="tags-condition-keys"></a>

These are the condition keys that you can use in an IAM permission policy to control access based on tags\. These condition keys let you compare the tags on the principal calling the operation, the tags provided to operation as a parameter, and the tags attached to the resource that would be access by the operation\.

See the page linked by the **Condition key name** for complete details about that condition key and how to use it\.


| Condition key name | Description | 
| --- | --- | 
|  [aws:PrincipalTag](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-principaltag)  |  Compares the tag attached to the principal \(IAM user or role\) making the request with the tag that you specify in the policy\.  | 
| [aws:RequestTag](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag) | Compares the tag key\-value pair that was passed to the request as a parameter with the tag pair that you specify in the policy\. | 
|  [aws:ResourceTag](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  |  Compares the tag key\-value pair that you specify in the policy with the key\-value pair that is attached to the resource\.  | 
| [aws:TagKeys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys) | Compares only the tag keys in a request with the keys that you specify in the policy\.  | 

## Example IAM policies that use tags<a name="tags-iam-policy-examples"></a>

**Example 1: Force users to attach a specific tag when they create a resource**  
The following example IAM permission policy shows how to force the user who creates or modifies an IAM policy's tags to include a tag with the key `Owner` and the value set to the individuals AWS user name\. If those conditions are not met, then the policy does not match and operation is not allowed\.  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "TagCustomerManagedPolicies",
            "Effect": "Allow",
            "Action": [
                "iam:CreatePolicy",
                "iam:TagPolicy"
            ],
            "Resource": "arn:aws:iam::123456789012:policy/*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestTag/Owner": "${aws:username}"
                }
            }
        }
    ]
}
```

**Example 2: Use tags to limit access to a resource to its "owner"**  
The following example IAM permission policy lets the user stop a running Amazon EC2 instance only if the user is tagged as the owner of that instance\.  
This example is an example of "attribute\-based access control"\. For more information and additional examples of using IAM policies to implement an tag\-based access control strategy, see [Controlling access to AWS resources using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) and [Controlling access to and for IAM users and roles using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_iam-tags.html), both in the *IAM User Guide*\. There is also a much more comprehensive tutorial that shows how to grant access to different projects and groups using multiple tags at [IAM tutorial: Define permissions to access AWS resources based on tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html)  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor1",
      "Effect": "Allow",
      "Action": [
        "ec2:StopInstances"
      ],
      "Resource": [
        "arn:aws:iam::123456789012:instance/*"
      ],
      "Condition": {
        "StringEquals": {
          "aws:ResourceTag/Owner": "${aws:username}"
        }
      }
    }
  ]
}
```