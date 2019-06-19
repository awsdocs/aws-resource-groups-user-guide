# Viewing Insights about AWS Resource Groups<a name="viewing-group-insights"></a>

Insights show detailed information about the resources in your groups, such as AWS CloudTrail logs, and results of evaluations against AWS Config rules\. AWS Trusted Advisor reports and the Personal Health Dashboard show events and recommendations at the account level\. The AWS CloudTrail and AWS Config views show information about a single, selected resource group at a time\.

**Topics**
+ [Included Insights](#w4aab5c34b7)
+ [Amazon CloudWatch Dashboards](#w4aab5c34b9)
+ [AWS Systems Manager Inventory and Compliance](#w4aab5c34c11)

## Included Insights<a name="w4aab5c34b7"></a>

Choosing **Insights** in the AWS Systems Manager left navigation pane shows monitoring views that are built\-in, or included by default\. Choose a resource group, and the page displays group members' rule compliance from AWS Config, or event log data from CloudTrail\. The Personal Health Dashboard shows events by region in your account\. Recommendations from Trusted Advisor are also per account\. The following shows an example of a Trusted Advisor view for an account\.

![\[Trusted Advisor view\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-insights-ta.png)

On the AWS Config tab, data includes rule compliance, compliance by resource type, and a history of configuration changes on group resources\.

For more information about how to drill down, interpret, and use the data shown by these insights, see the following AWS User Guides\.
+ [http://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html](http://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)
+ [http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)
+ [http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html#trusted-advisor](http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html#trusted-advisor)

## Amazon CloudWatch Dashboards<a name="w4aab5c34b9"></a>

The Dashboards by CloudWatch page in AWS Systems Manager shows data directly from the CloudWatch service\.

**To create a CloudWatch dashboard in the AWS Systems Manager console**

1. On the **Dashboard by CloudWatch** page, choose **Create new dashboard**\.

1. Enter a name for the dashboard, such as the name of the service for which you want to view CloudWatch data\.

1. Choose **Create dashboard**\.

1. Choose the graphical format in which you want CloudWatch displayed, and then choose **Configure**\.

For more information about how to use and change CloudWatch metrics, see the [http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)\.

## AWS Systems Manager Inventory and Compliance<a name="w4aab5c34c11"></a>

The **Inventory** insights show software and packages \(excluding AWS components\) that are installed on instances in a group that you are managing with AWS Systems Manager, or that are tagged with a tag that you specify in the search box at the top of the page\. The following screenshot shows an example of operating systems that are installed in the inventory of a group's instances\.

![\[Operating system inventory of a resource group\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/rg-inventory-osversion.png)

Inventory data comes from AWS Systems Manager\. For more information about how to work with inventory data, see [Systems Manager Inventory Management](http://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-inventory.html) in the *AWS Systems Manager User Guide*\.

The **Compliance** insights show compliance with patch and configuration standards that you set by using AWS Systems Manager\. For more information about how to set up patch baselines and configuration associations against which tagged or grouped resources can be measured, see [Systems Manager Configuration Compliance](http://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-compliance.html) in the *AWS Systems Manager User Guide*\.