# What Is AWS Resource Groups?<a name="welcome"></a>

You can organize your AWS resources, and make it easier to manage and automate tasks on large numbers of resources at one time, by working with *resource groups*\. This guide shows you how to create and manage resource groups in AWS Resource Groups\.

You can access Resource Groups through any of the following entry points\.

+ On the navigation bar of the [AWS Management Console](https://console.aws.amazon.com/console/home), at the upper left\.

+ In the AWS Systems Manager console, from the left navigation pane entry for Resource Groups\.

+ By using the Resource Groups API, in AWS CLI commands or AWS SDK programming languages\.

**To work with resource groups on the AWS Management Console home**

1. Sign in to the AWS Management Console\.

1. On the navigation bar, choose **Resource Groups**\.  
![\[AWS Console home with Resource Groups menu open.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-entry-consolehome.png)

1. Choose the an existing resource group from **Saved Groups**, or choose **Create a Group**\.

**To work with resource groups in AWS Systems Manager**

1. Sign in to the AWS Management Console\.

1. On the console home page, in the **Management Tools** area, choose **AWS Systems Manager**\.

1. On the **AWS Systems Manager** home page, choose **Explore Resource Groups**\.


+ [What Are Resource Groups?](#resource-groups-intro)
+ [Supported Resources](supported-resources.md)
+ [Getting Started with AWS Resource Groups](gettingstarted.md)
+ [Update Groups in AWS Resource Groups](updating-resource-groups.md)
+ [Delete Groups from AWS Resource Groups](deleting-resource-groups.md)
+ [Viewing Insights about AWS Resource Groups](viewing-group-insights.md)

## What Are Resource Groups?<a name="resource-groups-intro"></a>

In AWS, a *resource* is an entity that you can work with\. Examples include an Amazon EC2 instance, an AWS CloudFormation stack, or an Amazon S3 bucket\. If you work with multiple resources, you might find it useful to manage them as a group rather than move from one AWS service to another for each task\. If you manage large numbers of related resources, such as EC2 instances that make up an application layer, you likely need to perform bulk actions on multiples of these resources at one time\. Examples of bulk actions might be applying updates or security patches, upgrading applications, opening or closing ports to network traffic, or collecting specific log and monitoring data from your fleet of instances\.

A *resource group* is a collection of AWS resources that are all in the same AWS region, and that match criteria provided in a query\. You build queries in the Resource Groups console, or pass them as arguments to Resource Groups commands in the AWS CLI\. *Queries* include lists of resources that are specified in the following format `AWS::service::resource`, and tags\. *Tags* are keys that help identify and sort your resources within your organization; optionally, tags include values for keys\.

By default, the AWS Management Console is organized by AWS service\. But with Resource Groups, you can create a custom console that organizes and consolidates information based on criteria that you specify in tags\. The following list describes some of the cases in which tagging and resource grouping can help organize your resources\.

+ An application that has different phases, such as development, staging, and production

+ Projects managed by multiple departments or individuals

+ A set of AWS resources that you use together for a common project, or that you want to manage or monitor as a group

+ A set of resources related to applications that run on a specific platform, such as Android or iOS

For example, you are developing a web application, and you are maintaining separate sets of resources for your alpha, beta, and release stages\. Each version runs on Amazon EC2 with an Amazon Elastic Block Store storage volume\. You use Elastic Load Balancing to manage traffic and Route 53 to manage your domain\. Without Resource Groups, you might have to access multiple consoles just to check the status of your services or modify the settings for one version of your application\.

With Resource Groups, you use a single page to view and manage your resources\. For example, let’s say you use the tool to create a resource group for each version—alpha, beta, and release—of your application\. To check your resources for the alpha version of your application, open your resource group\. Then view the consolidated information on your resource group page\. To modify a specific resource, choose the resource's links on your resource group page to access the service console that has the settings that you need\.

### How Resource Groups Work<a name="how-resourcegroups-works"></a>

A resource group is a collection of specified types of resources that share one or more *tags* or portions of tags\. To create a resource group, you build a query that identifies the resource types you want that have tags that members of the group should have in common\.

The new Resource Groups feature permissions are at the account level, so as long as users sharing your account have the correct IAM permissions, they can work with resource groups that you create\. In the older, classic Resource Groups, however, if you use AWS Identity and Access Management \(IAM\) to create multiple users in the same account, those users have their own individual resource groups\. These groups are not visible to other users\. For information about creating IAM users, see [Creating an IAM User](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_SettingUpUser.html) in the *IAM User Guide*\.

Tags function as properties of a resource, so they are shared across your entire account\. Users in a department can draw from a common vocabulary \(tags\) within the department or account to create resource groups that are meaningful to their roles and responsibilities\. Having a common pool of tags also means that when users share a resource group, they don't have to worry about missing or conflicting tag information\.

### How Tagging Works<a name="how-tagging-works"></a>

Tags are key and value pairs that act as metadata for organizing your AWS resources\. With most AWS resources, you have the option of adding tags when you create the resource, whether it's an Amazon EC2 instance, an Amazon S3 bucket, or other resource\. However, you can also add tags to multiple resources at once by using Tag Editor\. You build a query for resources of various types, and then add, remove, or replace tags for the resources in your search results\. Queries assign an `AND` operator to tags, so any resource that matches the specified resource types and all specified tags is returned by the query\.

For more information about tagging, see [Working with Tag Editor](tag-editor.md) in this guide\. For more information about tagging, see [Tag Basics](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html#tag-basics) in the *Amazon EC2 User Guide for Linux Instances*\.