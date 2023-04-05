# Turning on group lifecycle events in Resource Groups<a name="monitor-groups-turn-on"></a>

 \(edited\) 

To receive notifications about lifecycle changes to your resource groups, you can on group lifecycle events\. Resource Groups then provides information about your groups' changes to Amazon EventBridge\. In EventBridge, you can evaluate and act on the changes using [rules you define in the EventBridge service](monitor-groups-create-rule.md)\.

**Minimum permissions**  
To turn on group lifecycle events in your AWS account, you must sign in as an AWS Identity and Access Management \(IAM\) principal with the following permissions:  
`resource-groups:UpdateAccountSettings`
`iam:CreateServiceLinkedRole`
`events:PutRule`
`events:PutTargets`
`events:DescribeRule`
`events:ListTargetsByRule`
`cloudformation:DescribeStacks`
`cloudformation:ListStackResources`
`tag:GetResources`

When you initially turn on group lifecycle events in an AWS account, Resource Groups creates a [service\-linked role named `AWSServiceRoleForResourceGroups`](security_iam_service-linked-roles.md)\. This managed role has permission to use a Resource Groups managed EventBridge rule\. The rule monitors the tags attached to your resources and the AWS CloudFormation stacks in your account for any changes\. Resource Groups then publishes those changes to the default event bus in Amazon EventBridge\. The service also creates an EventBridge managed rule named `[Managed\.ResourceGroups\.TagChangeEvents](https://console.aws.amazon.com/events/home#/eventbus/default/rules/Managed.ResourceGroups.TagChangeEvents)`\. This rule captures the details of tag changes of your resources\. This lets Resource Groups generate membership events to send to EventBridge for your custom rules to process\. Your EventBridge rules can then respond to events by sending notifications to the rules' configured targets\.

After you complete these steps, rules that look for these events should start receiving them in a few minutes\.

You can turn on group lifecycle events by using either the AWS Management Console or by using a command from the AWS CLI or one of the SDK APIs\. 

------
#### [ AWS Management Console ]

**To turn on group lifecycle events in the Resource Groups console**

1. Open the **[Settings](https://console.aws.amazon.com/resource-groups/groups/settings)** page in the Resource Groups console\.

1. In the **Group lifecycle events** section, choose the switch next to **Notifications are turned off**\.

1. On the confirmation dialog, choose **Turn on notifications**\.

   The feature switch displays **Notifications are turned on**\.

That completes the first part of the process\. After you turn on event notifications, you can [create rules in Amazon EventBridge](monitor-groups-create-rule.md) that capture the events and send them to specific AWS services for processing\.

------
#### [ AWS CLI ]

**To turn on group lifecycle events by using the AWS CLI or the AWS SDKs**  
The following example show how to use the AWS CLI to turn on group lifecycle events in Resource Groups\. Enter the command with the service principal parameter exactly as shown\. The output shows both the current status and the desired status of the feature\.

```
$ aws resource-groups update-account-settings /
    --group-lifecycle-events-desired-status ACTIVE
{
    "AccountSettings": {
        "GroupLifecycleEventsDesiredStatus": "ACTIVE",
        "GroupLifecycleEventsStatus": "IN_PROGRESS"
    }
}
```

You can confirm that the feature is turned on by running the following example command\. When both status fields show the same value, then the operation is complete\.

```
$ aws resource-groups get-account-settings
{
    "AccountSettings": {
        "GroupLifecycleEventsDesiredStatus": "ACTIVE",
        "GroupLifecycleEventsStatus": "ACTIVE"
    }
}
```

For more information, see the following resources:
+ AWS CLI – [aws resource\-groups update\-account\-settings](https://docs.aws.amazon.com/cli/latest/reference/resource-groups/update-account-settings.html) and [aws resource\-groups get\-account\-settings](https://docs.aws.amazon.com/cli/latest/reference/resource-groups/get-account-settings.html)
+ API – [UpdateAccountSettings](https://docs.aws.amazon.com/ARG/latest/APIReference/API_UpdateAccountSettings.html) and [GetAccountSettings](https://docs.aws.amazon.com/ARG/latest/APIReference/API_GetAccountSettings.html)

------