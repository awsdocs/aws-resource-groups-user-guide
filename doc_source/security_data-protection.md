# Data Protection in AWS Resource Groups<a name="security_data-protection"></a>

The AWS [shared responsibility model](http://aws.amazon.com/compliance/shared-responsibility-model/) applies to data protection in AWS Resource Groups\. As described in this model, AWS is responsible for protecting the global infrastructure that runs all of the AWS Cloud\. You are responsible for maintaining control over your content that is hosted on this infrastructure\. This content includes the security configuration and management tasks for the AWS services that you use\. For more information about data privacy, see the [Data Privacy FAQ](http://aws.amazon.com/compliance/data-privacy-faq)\. For information about data protection in Europe, see the [AWS Shared Responsibility Model and GDPR](http://aws.amazon.com/blogs/security/the-aws-shared-responsibility-model-and-gdpr/) blog post on the *AWS Security Blog*\.

For data protection purposes, we recommend that you protect AWS account credentials and set up individual user accounts with AWS Identity and Access Management \(IAM\)\. That way each user is given only the permissions necessary to fulfill their job duties\. We also recommend that you secure your data in the following ways:
+ Use multi\-factor authentication \(MFA\) with each account\.
+ Use SSL/TLS to communicate with AWS resources\. We recommend TLS 1\.2 or later\.
+ Set up API and user activity logging with AWS CloudTrail\.
+ Use AWS encryption solutions, along with all default security controls within AWS services\.
+ Use advanced managed security services such as Amazon Macie, which assists in discovering and securing personal data that is stored in Amazon S3\.
+ If you require FIPS 140\-2 validated cryptographic modules when accessing AWS through a command line interface or an API, use a FIPS endpoint\. For more information about the available FIPS endpoints, see [Federal Information Processing Standard \(FIPS\) 140\-2](http://aws.amazon.com/compliance/fips/)\.

We strongly recommend that you never put sensitive identifying information, such as your customers' account numbers, into free\-form fields such as a **Name** field\. This includes when you work with Resource Groups or other AWS services using the console, API, AWS CLI, or AWS SDKs\. Any data that you enter into Resource Groups or other services might get picked up for inclusion in diagnostic logs\. When you provide a URL to an external server, don't include credentials information in the URL to validate your request to that server\.

## Data Encryption<a name="protection-encryption"></a>

Compared to other AWS services, AWS Resource Groups has a minimal attack surface, because it does not provide a way of changing, adding, or deleting AWS resources except for groups\. Resource Groups collects the following service\-specific information from you\.
+ Group names \(not encrypted, not private\)
+ Group descriptions \(not encrypted, but private\)
+ Member resources in groups \(these are stored in logs, which are not encrypted\)

### Encryption at Rest<a name="protection-encryption-rest"></a>

There are no additional ways of isolating service or network traffic specific to Resource Groups\. If applicable, use AWS\-specific isolation\. You can use the Resource Groups API and console in a VPC to help maximize privacy and infrastructure security\.

### Encryption in Transit<a name="protection-encryption-transit"></a>

AWS Resource Groups data is encrypted in transit to the service's internal database for backup\. This is not user\-configurable\.

### Key Management<a name="protection-key-management"></a>

AWS Resource Groups is not currently integrated with AWS Key Management Service and does not support customer master keys \(CMKs\)\.

## Internetwork Traffic Privacy<a name="protection-privacy"></a>

AWS Resource Groups uses HTTPS for all transmissions between Resource Groups users and AWS\. Resource Groups uses transport layer security \(TLS\) 1\.2, but also supports TLS 1\.0 and 1\.1\.