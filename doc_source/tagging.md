# Tagging your AWS resources<a name="tagging"></a>

Tags are key and value pairs that act as metadata for organizing your AWS resources\. With most AWS resources, you have the option of adding tags when you create the resource, whether it's an Amazon EC2 instance, an Amazon S3 bucket, or other resource\. However, you can also add tags to multiple, supported resources at once by using Tag Editor\. You build a query for resources of various types, and then add, remove, or replace tags for the resources in your search results\. Tag\-based queries assign an `AND` operator to tags, so any resource that matches the specified resource types and all specified tags is returned by the query\.

**Important**  
Do not store personally identifiable information \(PII\) or other confidential or sensitive information in tags\. We use tags to provide you with billing and administration services\. Tags are not intended to be used for private or sensitive data\.

You can tag [supported resources](supported-resources.md) by using Tag Editor, and some additional resources by using the tagging functionality provided by the service console in which you create and manage the resource\. See the documentation for each service to discover what tagging functionality that service provides\.

**Topics**
+ [Tags and Attribute\-based access control \(ABAC\)](#tagging-and-abac)
+ [Best practices for tag names](#id_tags_naming_best_practices)
+ [Tag Editor](tag-editor.md)
+ [Using tags in IAM permission policies](tags-in-iam-policies.md)
+ [AWS Organizations tag policies](tag-policies-orgs.md)

## Tags and Attribute\-based access control \(ABAC\)<a name="tagging-and-abac"></a>

Tags can be an important part of your AWS access control strategy\. To use tags as the "attributes" in an attribute\-based access control strategy, see [Controlling access to AWS resources using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) and [Controlling access to and for IAM users and roles using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_iam-tags.html), both in the *IAM User Guide*\.

There is also a much more comprehensive tutorial that shows how to grant access to different projects and groups using tags at [IAM tutorial: Define permissions to access AWS resources based on tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html) in the *IAM User Guide*\.

Also, if you use a SAML\-based identity provider \(IdP\) for single sign\-in to AWS, you can configure the SAML IdP to attach the tags to the assumed roles that it delivers to your users for access\. For more information, see [IAM tutorial: Use SAML session tags for ABAC](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_abac-saml.html) in the *AWS Identity and Access Management User Guide*\.

## Best practices for tag names<a name="id_tags_naming_best_practices"></a>

These are some best practices and naming conventions that we recommend that you use with your tags\.

Key names for AWS tags are case sensitive so ensure that they are used consistently\. For example, the tags keys `CostCenter` and `costcenter` are different, so one might be configured as a cost allocation tag for financial analysis and reporting and the other one might not be\. 

A number of tags are predefined by AWS or created automatically by various AWS services\. Many of these AWS\-defined *system tags* use key names that are all lowercase, with hyphens separating words in the name, and prefixes followed by colons to identify the source service for the tag\. For example: 
+ `aws:ec2spot:fleet-request-id` is a tag that identifies the Amazon EC2 Spot Instance Request that launched the instance\.
+ `aws:cloudformation:stack-name` is a tag that identifies the AWS CloudFormation stack that created the resource\. 
+ `elasticbeanstalk:environment-name` is a tag that identifies the application that created the resource\.

Consider naming your tags using the following rules:
+ All lowercase
+ Use hyphens to separate words
+ Use a prefix followed by a colon to identify the organization name or abbreviated name\. 

For example, for a fictitious company named *AnyCompany*, you might define tags such as:
+ `anycompany:cost-center` to identify the internal Cost Center code 
+ `anycompany:environment-type` to identify whether the environment is development, test, or production
+ `anycompany:application-id` to identify the application the resource was created for 

The prefix ensures that tags are clearly recognizable as defined by your organization and not by AWS or a third\-party tool that you may be using\. Using all lowercase with hyphens for separators avoids confusion about how to capitalize a tag name\. For example, `anycompany:project-id` is simpler to remember than `ANYCOMPANY:ProjectID`, `anycompany:projectID`, or `Anycompany:ProjectId`\.