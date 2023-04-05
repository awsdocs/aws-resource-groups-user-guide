# Creating an EventBridge rule to capture group lifecycle events and publish notifications<a name="monitor-groups-create-rule"></a>

You can [turn on group lifecycle events for your resource groups](monitor-groups-turn-on.md) in AWS Resource Groups to publish events to Amazon EventBridge\. Then, you can create EventBridge rules that respond to those events by sending them to other AWS services for further processing\.

**Note**  
Currently, you can create an EventBridge rule for AWS Resource Groups events only by using the AWS Command Line Interface \(AWS CLI\) or an AWS SDK\.

------
#### [ AWS CLI ]

The process to create a rule in EventBridge that captures events and sends them to your desired target service takes two separate CLI commands:

1. [Create the EventBridge rule to capture the events you want](#monitor-cli-create-rule)

1. [Attach a target that can process the events to the EventBridge rule ](#monitor-cli-attach-target)

Step 1: Create the EventBridge rule to capture the events  
The following AWS CLI `[put\-rule](https://docs.aws.amazon.com/cli/latest/reference/events/put-rule.html)` example command creates an EventBridge rule that captures ***all*** Resource Groups lifecycle event changes\.  

```
$ aws events put-rule \
    --name "CatchAllResourceGroupEvents" \
    --event-pattern '{"source":["aws.resource-groups"]}'
{
    "RuleArn": "arn:aws:events:us-east-1:123456789012:rule/CatchAllResourceGroupEvents"
}
```
The output includes the Amazon Resource Name \(ARN\) of the new rule\.  
Parameter values that include quoted strings have different formatting rules based on the operating system and shell that you use\. For the examples in this guide, we show commands that work on a Linux BASH shell\. For instructions about formatting strings with embedded quotes for other operating systems, such as the Windows command prompt, see [Using quotation marks inside strings](https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-parameters-quoting-strings.html#cli-usage-parameters-quoting-strings-containing) in the *AWS Command Line Interface User Guide*\.  
As parameter strings get more complex, it can be easier and less error prone to [accept a parameter value from a text file](https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-parameters-file.html) instead of typing it directly on the command line\.
The following event pattern restricts the events to only those that are related to the specified group, identified by its ARN\. This event pattern is a complex JSON string that is much less readable when compressed into a single\-line, properly escaped JSON string\. You can store it in a file instead\.  
Store the event pattern JSON string in a file\. In the following code example, the file is `eventpattern.txt`\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail": {
        "group": {
            "arn": [ "my-resource-group-arn" ]
        }
    }
}
```
Then, issue the following command to create the rule, retrieving the custom event pattern from the file\.  

```
$ aws events put-rule \
    --name "CatchResourceGroupEventsForMyGroup" \
    --event-pattern file://eventpattern.txt
{
    "RuleArn": "arn:aws:events:us-east-1:123456789012:rule/CatchResourceGroupEventsForMyGroup"
}
```
To capture other types of Resource Groups events, replace the `--event-pattern` string with filters like those presented in the section [Example EventBridge custom event patterns for different use cases](monitor-groups-syntax.md#monitor-groups-example-eventbridge-filters)\.

Step 2: Attach a target that can process the events to the EventBridge rule   
Now that you have a rule that captures the events of interest to you, you can attach one or more targets to do some type of processing on the events\.  
The following AWS CLI `[put\-targets](https://docs.aws.amazon.com/cli/latest/reference/events/put-targets.html)` command attaches an Amazon Simple Notification Service \(Amazon SNS\) topic named `my-sns-topic` to the rule you created in the previous example\. All subscribers to the topic receive a notification when a change occurs to the group specified in the rule\.  

```
$ aws events put-targets \
    --rule CatchResourceGroupEventsForMyGroup \
    --targets Id=1,Arn=arn:aws:sns:us-east-1:123456789012:my-sns-topic
{
    "FailedEntryCount": 0,
    "FailedEntries": []
}
```
At this point, any group changes that match the event pattern in your rule are automatically sent to the configured target or targets\. If, as in the previous example, the target is an Amazon SNS topic, then all subscribers to the topic receive a message containing the event as described in [Structure and syntax of Resource Groups lifecycle events](monitor-groups-syntax.md)\. 

For more information, see the following resources:
+ AWS CLI – [aws events put\-rule](https://docs.aws.amazon.com/cli/latest/reference/events/put-rule.html) and [aws events put\-targets](https://docs.aws.amazon.com/cli/latest/reference/events/put-targets.html)
+ API – [PutRule](https://docs.aws.amazon.com/eventbridge/latest/APIReference/API_PutRule.html) and [PutTargets](https://docs.aws.amazon.com/eventbridge/latest/APIReference/API_PutTargets.html)

------

## Creating a rule to capture only specific group lifecycle event types<a name="monitor-groups-create-rule-custom"></a>

You can create a rule with a custom event pattern that captures only the events that you are interested in\. For complete details about how to filter incoming events using a custom event pattern, see [Amazon EventBridge events](https://docs.aws.amazon.com/eventbridge/latest/userguide/eventbridge-and-event-patterns.html) in the *Amazon EventBridge User Guide*\.

For example, suppose you want a rule to process only those Resource Groups notifications that indicate the creation of a new resource group\. You could use a custom event pattern similar to the following example\.

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group State Change" ],
    "detail": {
        "state-change": "create"
    }
}
```

That filter captures only those events that have those exact values in the specified fields\. For a complete list of the fields available for you to match, see [Structure and syntax of Resource Groups lifecycle events](monitor-groups-syntax.md)\.