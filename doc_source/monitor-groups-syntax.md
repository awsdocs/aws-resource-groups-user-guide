# Structure and syntax of Resource Groups lifecycle events<a name="monitor-groups-syntax"></a>

The lifecycle events for AWS Resource Groups take the form of [JSON](https://json.org) object strings in the following general format\.

```
{
    "version": "0",
    "id": "08f00e24-2e30-ec44-b824-8acddf1ac868",
    "detail-type": "ResourceGroups Group ... Change",
    "source": "aws.resource-groups",
    "account": "123456789012",
    "time": "2020-09-29T09:59:01Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:resource-groups:us-east-1:123456789012:group/MyGroupName"
    ],
    "detail": {
        ...
    }
}
```

For details about the fields common to all Amazon EventBridge events, see [Amazon EventBridge events](https://docs.aws.amazon.com/eventbridge/latest/userguide/aws-events.html) in the *Amazon EventBridge User Guide*\. Details that are specific to Resource Groups are explained in the following table\.


| Field name | Type | Description | 
| --- | --- | --- | 
| detail\-type | String |  For Resource Groups, the `detail-type` field is always one of the following values: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/monitor-groups-syntax.html)  | 
| source | String | For Resource Groups, this value is always "aws\.resource\-groups"\. | 
| resources | An array of Amazon Resource Names \(ARNs\) |  This field always includes the [Amazon resource name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the group with the change that triggered this event\. This field can also include the ARNs of any resources added to or removed from the group, if applicable\.  | 
|  `detail`  | JSON object string | This is the payload of the event\. The contents of the detail field vary based on the value of the detail\-type\. [See the next section for more information\.](#monitor-groups-syntax-detail) | 

## Structure of the `detail` field<a name="monitor-groups-syntax-detail"></a>

The `detail` field includes all of the Resource Groups service\-specific details about a specific change\. The `detail` field can take one of two forms, a group state change or membership change, based on the value of the `detail-type` field described in the previous section\.

**Important**  
Resource groups in these events are identified by a combination of the group's ARN and a `"unique-id"` field that contains a [UUID](https://wikipedia.org/wiki/Universally_unique_identifier)\. By including a UUID as part of the identity of a resource group, you can distinguish between a group that is deleted and a different group that is later created with the same name\. We recommend that you treat a concatenation of the ARN and unique id as the key for the group in your programs that interact with these events\. 

### Group state change<a name="monitor-groups-syntax-detail-state-change"></a>

`"detail-type": "ResourceGroups Group State Change"`

This `detail-type` value indicates that the state of the group itself, including its metadata, has changed\. This change occurs when a group is created, updated, or deleted, as indicated by the `"change"` field within the `detail`\. 

The information included in the `details` section when this `detail-type` is specified include the fields described in the following table\.


| Field name | Type | Description | 
| --- | --- | --- | 
| event\-sequence | Double | A monotonically increasing number that specifies the sequence of events for a specific group\. The number resets when you delete the group and create another group with the same name\.  | 
| group | [`Group`](#monitor-groups-syntax-detail-group-object) JSON object | The group object associated with the event by its ARN, name, and unique ID\. | 
| state\-change | String | The type of state change that occurred\. Can be any of the following values:[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/monitor-groups-syntax.html) | 
| old\-state  | GroupState JSON object | The state of the group before the change\. The object includes only the values of properties that changed\.  | 
|  `new-state`  | GroupState JSON object | The state of the group after the change\. The object includes only the values of properties that changed\. | 

The `group` JSON object contains the elements described in the following table\. 


| Field name | Type | Description | 
| --- | --- | --- | 
| arn | String | The ARN of the group\. | 
| name | String | The friendly name of the group\. | 
| unique\-id | GUID | A unique GUID value that distinguishes between a group that was deleted and a different group that was later created with the same name and ARN\. Use the concatenation of ARN and this value as a unique key for the group when consuming these events in your code\.  | 

The `GroupState` JSON objects contain the elements described in the following table\.


| Field name | Type | Description | 
| --- | --- | --- | 
| description | String | The customer\-provided description of the resource group\. | 
| resource\-query | ResourceQuery JSON object | A JSON representation of the query that defines the group's members\. This field is present only for groups based on a query\. The syntax of this field is defined by the [ResourceQuery API data type](https://docs.aws.amazon.com/organizations/latest/APIReference/API_ResourceQuery.html)\. Example of this are included in the [Create](#monitor-groups-syntax-detail-state-change-create) and [Update](#monitor-groups-syntax-detail-state-change-update) event examples\. | 
| group\-configuration | Configuration JSON object | A JSON representation of configuration parameters associated with a service\-linked group\. For more information, see [Service configurations for resource groups](https://docs.aws.amazon.com/ARG/latest/APIReference/about-slg.html) in the AWS Resource Groups API Reference\. | 

Each of the following code examples illustrates the contents of the `detail` field for each `state-change` type\.

#### Create<a name="monitor-groups-syntax-detail-state-change-create"></a>

`"state-change": "create"` 

The event indicates that a new group was created\. The event carries all the group metadata properties set during the group's creation\. This event is typically followed by one of more group membership events unless the group is empty\. Properties that have a null value are not displayed in the event body\. 

The following example event indicates a newly created resource group named `my-service-group`\. In this example, the group uses a tag\-based query that matches only Amazon Elastic Compute Cloud \(Amazon EC2\) instances that have the tag `"project"="my-service"`\.

```
{
    "version": "0",
    "id": "08f00e24-2e30-ec44-b824-8acddf1ac868",
    "detail-type": "ResourceGroups Group State Change",
    "source": "aws.resource-groups",
    "account": "123456789012",
    "time": "2020-09-29T09:59:01Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:resource-groups:us-east-1:123456789012:group/my-service-group"
    ],
    "detail": {
        "event-sequence": 1.0,
        "state-change": "create", 
        "group": {
            "arn": "arn:aws:resource-groups:us-east-1:123456789012:group/my-service-group",
            "name": "my-service-group",
            "unique-id": "3dd07ab7-3228-4410-8cdc-6c4a10fcceea"
        },        
        "new-state": {
            "resource-query": {
                "type": "TAG_FILTERS_1_0",
                "query": "{
                    \"ResourceTypeFilters\": [\"AWS::EC2::Instance\"],
                    \"TagFilters\": [{\"Key\":\"project\", \"Values\":[\"my-service\"}]
                }"
            }
        }
    }
}
```

#### Update<a name="monitor-groups-syntax-detail-state-change-update"></a>

`"state-change": "update"`

The event indicates that an existing group was modified in some way\. The event carries only the properties that changed from the previous state\. Properties that have not changed are not displayed in the event body\.

The following example event indicates that the tag\-based query in the previous example's resource group was modified to also include Amazon EC2 volume resources in the group\.

```
{
    "version": "0",
    "id": "08f00e24-2e30-ec44-b824-8acddf1ac868",
    "detail-type": "ResourceGroups Group State Change",
    "source": "aws.resource-groups",
    "account": "123456789012",
    "time": "2020-09-29T09:59:01Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:resource-groups:us-east-1:123456789012:group/my-service-group"
    ],
    "detail": {
        "event-sequence": 3.0,
        "state-change": "update",
        "group": {
            "arn": "arn:aws:resource-groups:us-east-1:123456789012:group/my-service-group",
            "name": "my-service",
            "unique-id": "3dd07ab7-3228-4410-8cdc-6c4a10fcceea"
        },        
        "new-state": {
            "resource-query": {
                "type": "TAG_FILTERS_1_0",
                "query": "{
                    \"ResourceTypeFilters\": [\"AWS::EC2::Instance\", \"AWS::EC2::Volume\"],
                    \"TagFilters\": [{\"Key\":\"project\", \"Values\":[\"my-service\"}]
                }"
            }
        },
        "old-state": {
            "resource-query": {
                "type": "TAG_FILTERS_1_0",
                "query": "{
                    \"ResourceTypeFilters\": [\"AWS::EC2::Instance\"],
                    \"TagFilters\": [{\"Key\":\"Project\", \"Values\":[\"my-service\"}]
                }"
            }
        }
    }
}
```

#### Delete<a name="monitor-groups-syntax-detail-state-change-delete"></a>

`"state-change": "delete"`

The event indicates that an existing group was deleted\. The detail field includes no metadata about the group other than its identification\. The `event-sequence` field is reset after this event as it is, by definition, the last event for this `arn` and `unique-id`\.

```
{
    "version": "0",
    "id": "08f00e24-2e30-ec44-b824-8acddf1ac868",
    "detail-type": "ResourceGroups Group State Change",
    "source": "aws.resource-groups",
    "account": "123456789012",
    "time": "2020-09-29T09:59:01Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:resource-groups:us-east-1:123456789012:group/my-service"
    ],
    "detail": {
        "event-sequence": 4.0,   
        "state-change": "delete",
        "group": {
            "arn": "arn:aws:resource-groups:us-east-1:123456789012:group/my-service",
            "name": "my-service",
            "unique-id": "3dd07ab7-3228-4410-8cdc-6c4a10fcceea"
        }
    }
}
```

### Group membership change<a name="monitor-groups-syntax-detail-membership-change"></a>

`"detail-type": "ResourceGroups Group Membership Change"`

This `detail-type` value indicates that the group's membership was changed by a resource being added to or removed from the group\. When this `detail-type` is specified, the top\-level `resources` field includes the ARN of the group whose membership was changed and the ARNs of any resources that were added to or removed from the group\.

The information included in the `details` section when this `detail-type` is specified include the fields described in the following table\.


| Field name | Type | Description | 
| --- | --- | --- | 
| event\-sequence | Double | A monotonically increasing number that indicates the sequence of events for a specific group\. The number resets when the group is deleted and its unique ID changes\.  | 
| group | Group JSON object | Identifies the group object associated with the event by its ARN, name, and unique ID\. | 
|  `resources`  | Array of ResourceChange JSON objects |  An array of resources whose group membership has changed\. This `ResourceChange` object contains the following fields for each resource: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ARG/latest/userguide/monitor-groups-syntax.html)  | 

The following code example illustrates the contents of the event for a typical membership change type\. This example shows one resource being added to the group, and one resource being removed from the group\.

```
{
    "version": "0",
    "id": "08f00e24-2e30-ec44-b824-8acddf1ac868",
    "detail-type": "ResourceGroups Group Membership Change",
    "source": "aws.resource-groups",
    "account": "123456789012",
    "time": "2020-09-29T09:59:01Z",
    "region": "us-east-1",
    "resources": [
        "arn:aws:resource-groups:us-east-1:123456789012:group/my-service",
        "arn:aws:ec2:us-east-1:123456789012:instance/i-abcd1111",
        "arn:aws:ec2:us-east-1:123456789012:instance/i-efef2222"
    ],
    "detail": {
        "event-sequence": 2.0,
        "group": {
            "arn": "arn:aws:resource-groups:us-east-1:123456789012:group/my-service",
            "name": "my-service",
            "unique-id": "3dd07ab7-3228-4410-8cdc-6c4a10fcceea"
        },
        "resources": [
            {
                "membership-change": "add",
                "arn": "arn:aws:ec2:us-east-1:123456789012:instance/i-abcd1111",
                "resource-type": "AWS::EC2::Instance"
            },
            {
                "membership-change": "remove",
                "arn": "arn:aws:ec2:us-east-1:123456789012:instance/i-efef2222",
                "resource-type": "AWS::EC2::Instance"
            }
        ]
    }
}
```

## Example EventBridge custom event patterns for different use cases<a name="monitor-groups-example-eventbridge-filters"></a>

The following example EventBridge custom event patterns filter the events generated by Resource Groups to only those that you are interested in for a specific event rule and target\.

In the following code examples, if a specific group or resource is needed, replace each *user input placeholder* with your own information\.

All Resource Groups events  

```
{
    "source": [ "aws.resource-groups" ]
}
```

Group state or membership change events  
The following code example is for all group *state* changes\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group State Change " ]
}
```
The following code example is for all group *membership* changes\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group Membership Change" ]
}
```

Events for a specific group  

```
{
    "source": [ "aws.resource-groups" ],
    "detail": {
        "group": {
            "arn": [ "my-group-arn" ]
        }
    }
}
```
The previous example captures changes to the specified group\. The following example does the same and also captures changes when the group is a member resource of another group\.  

```
{
    "source": [ "aws.resource-groups" ],
    "resources": [ "my-group-arn" ]
}
```

Events for a specific resource  
You can filter only group membership change events for specific member resources\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group Membership Change " ],
    "resources": [ "arn:aws:ec2:us-east-1:123456789012:instance/i-b188560f" ]
}
```

Events for a specific resource type  
You can use prefix matching with ARNs to match events for a specific resource type\.  

```
{
    "source": [ "aws.resource-groups" ],
    "resources": [
        { "prefix": "arn:aws:ec2:us-east-1:123456789012:instance" } 
    ]
}
```
Alternatively, you can use exact matching by using `resource-type` identifiers, potentially matching on more than one type concisely\. Unlike the previous example, the following example matches only group membership change events because group state change events don't include a `resources` field in their `detail` field\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail": {
        "resources": [
            {
                "resource-type": [ "AWS::EC2::Instance", "AWS::EC2::Volume" ]
            }
        ]
    }
}
```

All resource removal events  

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group Membership Change" ],
    "detail": {
        "resources": [
            {
                "membership-change": [ "remove" ]
            }
        ]
    }
}
```

All resource removal events for a specific resource  

```
 {
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group Membership Change" ],
    "detail": {
        "resources": [
            {
                "membership-change": [ "remove" ],
                "arn": [ "arn:aws:ec2:us-east-1:123456789012:instance/i-b188560f" ]
            }
        ]
    }
}
```
You can't use the **top\-level** `resources` array that was used in the first example in this section for this type of event filtering\. That's because a resource in the top\-level `resources` element might be a resource being added to a group and the event would still match\. In other words, the following code example might return unexpected events\. Instead, use the syntax shown in the previous example\.  

```
{
    "source": [ "aws.resource-groups" ],
    "detail-type": [ "ResourceGroups Group Membership Change" ],
    "resources": [ "arn:aws:ec2:us-east-1:123456789012:instance/i-b188560f" ],
    "detail": {
        "resources": [
            {
                "membership-change": [ "remove" ]
            }
        ]
    }
}
```