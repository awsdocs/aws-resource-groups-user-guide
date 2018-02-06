# Prerequisites for Working with AWS Resource Groups<a name="gettingstarted-prereqs"></a>

Before you get started working with resource groups, be sure you have an active AWS account with existing resources, and appropriate rights to tag resources and create groups\.


+ [Sign Up for AWS](#w3ab1b5c19c13b7)
+ [Create Resources](#w3ab1b5c19c13b9)
+ [Setting Up Permissions](#rg-permissions)

## Sign Up for AWS<a name="w3ab1b5c19c13b7"></a>

If you do not have an AWS account, use the following procedure to create one\.

**To sign up for AWS**

1. Open [https://aws\.amazon\.com/](https://aws.amazon.com/) and choose **Create an AWS Account**\.

1. Follow the online instructions\.

## Create Resources<a name="w3ab1b5c19c13b9"></a>

You can create an empty resource group, but won't be able to see insights or perform any tasks on resource group members until there are resources in the group\. For more information about the supported resource types, see \.

## Setting Up Permissions<a name="rg-permissions"></a>

To make full use of Resource Groups and Tag Editor, you might need additional permissions to tag resources or to see a resource's tag keys and values\. These permissions fall into the following categories: 

+ Permissions for individual services so that you can tag resources from those services and include them in resource groups\.

+ Permissions that are are required to use the Tag Editor console and API\.

+ Permissions that are required to use the new AWS Resource Groups console and API\. 

**Note**  
The managed policies that were used for legacy Resource Groups, `ResourceGroupsandTagEditorFullAccess` and `ResourceGroupsandTagEditorReadOnlyAccess`, do not grant access to AWS Resource Groups\.

If you are an administrator, you can provide permissions for your users by creating policies through the AWS Identity and Access Management \(AWS IAM\) service\. You first create IAM users or groups, and then apply the policies with the permissions that they need\. For general information about creating and attaching IAM policies, see [Working with Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/ManagingPolicies.html)\.

### Permissions for Individual Services<a name="rg-perms-individual-services"></a>

**Important**  
 This section describes permissions required for individual services if you want to tag resources from those services' consoles and APIs and include them in resource groups\.

As described in [What Are Resource Groups?](welcome.md#resource-groups-intro), each resource group represents a collection of resources of specified types that share one or more tag keys or values\. To add tags to a resource, you need the necessary permissions for the service to which the resource belongs\. For example, to tag Amazon EC2 instances, your must have permissions to the tagging actions in that service's API, such as those listed in the [Amazon EC2 user guide](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html#Using_Tags_CLI)\.

To make full use of the Resource Groups feature, you need other permissions that allow you to access a service's console and interact with the resources there\. For examples of such policies for Amazon EC2, see [Example Policies for Working in the Amazon EC2 Console](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policies-ec2-console.html) in the *Amazon EC2 User Guide for Linux Instances*\.

### Granting Permissions for Using Tag Editor<a name="w3ab1b5c19c13c11c13"></a>

For information about how to grant permissions for Tag Editor and the legacy Resource Groups console, see [Obtaining Permissions for Resource Groups and Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/obtaining-permissions-for-resource-groups.html) in the AWS Management Console Help\. Permissions shown in this topic are for using the new AWS Resource Groups service\.

### Granting Permissions for Using AWS Resource Groups<a name="w3ab1b5c19c13c11c15"></a>

This section describes required permissions for the new AWS Resource Groups service\. For information about how to assign permissions for using legacy Resource Groups, see [Obtaining Permissions for Resource Groups and Tag Editor](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/obtaining-permissions-for-resource-groups.html)\. The managed policies that were used for legacy Resource Groups, `ResourceGroupsandTagEditorFullAccess` and `ResourceGroupsandTagEditorReadOnlyAccess`, do not grant access to AWS Resource Groups\.

To add a policy for using AWS Resource Groups to a user, do the following\.

1. Open the [IAM console](https://console.aws.amazon.com/iam/home?#home)\.

1. In the navigation pane, choose **Users**\.

1. Find the user to whom you want to grant AWS Resource Groups permissions\. Choose the user's name to open the user properties page\.

1. Choose **Add permissions**\.

1. Choose **Attach existing policies directly**\.  
![\[IAM attach policies.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-iam-addperms.png)

1. Choose **Create policy**\.

1. On the **JSON** tab, paste the following policy statement\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": [
           "ec2:DescribeInstances",
           "ec2:DescribeSecurityGroups",
           "ec2:DescribeSnapshots",
           "ec2:DescribeVolumes",
           "ec2:DescribeVpcs",
           "elasticache:DescribeCacheClusters",
           "elasticache:DescribeSnapshots",
           "elasticache:ListTagsForResource",
           "elasticloadbalancing:DescribeLoadBalancers",
           "elasticloadbalancing:DescribeTags",
           "elasticmapreduce:DescribeCluster",
           "elasticmapreduce:ListClusters",
           "kinesis:DescribeStream",
           "kinesis:ListStreams",
           "kinesis:ListTagsForStream",
           "opsworks:DescribeStacks",
           "opsworks:ListTags",
           "rds:DescribeDBInstances",
           "rds:DescribeDBSnapshots",
           "rds:ListTagsForResource",
           "redshift:DescribeClusters",
           "redshift:DescribeTags",
           "resource-groups:*",
           "route53:GetHealthCheck",
           "route53:GetHostedZone",
           "route53:ListHealthChecks",
           "route53:ListHostedZones",
           "route53:ListTagsForResource",
           "route53domains:ListDomains",
           "s3:GetBucketTaggingConfiguration",
           "s3:ListBuckets",
           "storagegateway:DescribeGatewayInformation",
           "storagegateway:ListGateways",
           "storagegateway:ListTagsForResource",
           "tag:GetResources"
         ],
         "Resource": "*"
       }
     ]
   }
   ```
**Note**  
This policy statement grants permissions only for AWS Resource Groups actions\. It does not allow access to AWS Systems Manager tasks in the AWS Resource Groups console\. For example, this policy does not grant permissions for you to use Systems Manager Automation commands\. To perform Systems Manager tasks on resource groups, you must have Systems Manager permissions attached to your policy \(such as `ssm:*`\)\. For more information about granting access to Systems Manager, see [Configuring Access to Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-access.html) in the *Systems Manager User Guide*\.

1. Choose **Review policy**\.

1. Give the new policy a name and description\. To distinguish this policy from any policies for legacy Resource Groups, the name should be different from `ResourceGroupsandTagEditorFullAccess`\. For example, `AWSResourceGroupsQueryAPIAccess`\.  
![\[IAM review policy name and description.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-iam-policyname.png)

1. Choose **Create policy**\.

1. Now that the policy is saved in IAM, you can attach it to other users\. For more information about how to add a policy to a user, see [Adding Permissions by Attaching Policies Directly to the User](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#by-direct-attach-policy) in the *IAM User Guide*\.