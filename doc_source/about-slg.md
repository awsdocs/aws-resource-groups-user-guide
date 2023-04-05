# Service configurations for resource groups<a name="about-slg"></a>

Resource groups enable you to manage collections of your AWS resources as a unit\. Some AWS services support this by performing requested operations on all members of the group\. Such services can store the settings to be applied to group members as a *configuration* in the form of a [JSON](https://www.json.org/) data structure that is attached to the group\.

This topic describes the available configuration settings for supported AWS services\.

**Topics**
+ [How to access the service configuration attached to a resource group](#about-slg-how-to-access)
+ [JSON syntax of a service configuration](#about-slg-config-syntax)
+ [Supported configuration types and parameters](#about-slg-types)

## How to access the service configuration attached to a resource group<a name="about-slg-how-to-access"></a>

Services that support service\-linked groups typically set the configuration for you when you use the tools provided by that service, such as that service's management console or its AWS CLI and AWS SDK operations\. Some services fully manage their service\-linked groups and you can't modify them in any way except as allowed by the console or commands provided by the owning AWS service\. However, in some cases, you can interact with the service configuration by using the following API operations in the AWS SDKs or their AWS CLI equivalents:
+ You can attach your own configuration to a group when you create the group by using the `[CreateGroup](https://docs.aws.amazon.com/ARG/latest/APIReference/API_CreateGroup.html)` operation\.
+ You can modify the current configuration attached to a group by using the `[PutGroupConfiguration](https://docs.aws.amazon.com/ARG/latest/APIReference/API_PutGroupConfiguration.html)` operation\.
+ You can view the current configuration of a resource group by calling the `[GetGroupConfiguration](https://docs.aws.amazon.com/ARG/latest/APIReference/API_GetGroupConfiguration.html)` operation\.

## JSON syntax of a service configuration<a name="about-slg-config-syntax"></a>

A resource group can contain a *configuration* that defines service\-specific settings that apply to the resources that are members of that group\.

A configuration is expressed as a [JSON](https://www.json.org/) object\. At the top\-most level, a configuration is an array of [group configuration items](https://docs.aws.amazon.com/ARG/latest/APIReference/API_GroupConfigurationItem.html)\. Each group configuration item contains two elements: a `Type` for the configuration and a set of `Parameters` defined by that type\. Each parameter contains a `Name` and an array of one or more `Values`\. The following example with *placeholders* shows the basic syntax for a configuration for a single sample resource type\. This example shows a type with two parameters, and each parameter with two values\. The actual valid types, parameters, and values are discussed in the next section\.

```
{
    "Configuration": [
        {
            "Type": "configuration-type",
            "Parameters": [
                {
                    "Name": "parameter1-name",
                    "Values": [
                        "value1",
                        "value2"
                    ]
                },
                {
                    "Name": "parameter2-name",
                    "Values": [
                        "value3",
                        "value4"
                    ]
                }
            ]
        }
    ]
}
```

## Supported configuration types and parameters<a name="about-slg-types"></a>

Resource Groups supports using the following configuration types\. Each configuration type has a set of parameters that are valid for that type\.

**Topics**
+ [`AWS::ResourceGroups::Generic`](#about-slg-types-generic)
+ [`AWS::AppRegistry::Application`](#about-slg-types-appregistry)
+ [`AWS::CloudFormation::Stack`](#about-slg-types-cloudformation)
+ [`AWS::EC2::CapacityReservationPool`](#about-slg-types-ec2-capacityreservation)
+ [`AWS::EC2::HostManagement`](#about-slg-types-resourcegroups-ec2-hostmanagement)
+ [`AWS::NetworkFirewall::RuleGroup`](#about-slg-types-network-firewall-rulegroup)

### `AWS::ResourceGroups::Generic`<a name="about-slg-types-generic"></a>

This configuration type specifies settings that enforce membership requirements on the resource group, rather than configuring the behavior of a specific resource type for an AWS service\. This configuration type is automatically added by those service\-linked groups that need it, such as the `AWS::EC2::CapacityReservationPool` and `AWS::EC2::HostManagment` types\.

The following `Parameters` are valid for the `AWS::ResourceGroups::Generic` service\-linked group `Type`\.
+ **`allowed-resource-types`**

  This parameter specifies that the resource group can consist of resources of only the specified type or types\.

  **Data type of values:** String

  **Permitted values:**
  + `AWS::EC2::Host` – A `Configuration` with this parameter and value is required when the service configuration also contains a `Configuration` of type `AWS::EC2::HostManagement`\. This ensures that the `HostManagement` group can contain only Amazon EC2 dedicated hosts\.
  + `AWS::EC2::CapacityReservation` – A `Configuration` with this parameter and value is required when the service configuration also contains a `Configuration` item of type `AWS::EC2::CapacityReservationPool`\. This ensures that a `CapacityReservation` group can contain only Amazon EC2 capacity reservation capacity\.

  **Required:** Conditional, based on other `Configuration` elements that are attached to the resource group\. See the previous entry for **Permitted values**\.

  The following example restricts group members to only Amazon EC2 host instances\.

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": ["AWS::EC2::Host"]
                  }
              ]
          }
      ]
  }
  ```
+ **`deletion-protection`**

  This parameter specifies that the resource group can't be deleted unless it contains no members\. For more information, see [Delete a host resource group](https://docs.aws.amazon.com/license-manager/latest/userguide/host-resource-groups.html#host-resource-group-delete) in the *License Manager User Guide*

  **Data type of values:** Array of string

  **Permitted values:** The only permitted value is `[ "UNLESS_EMPTY" ]` \(the value must be upper case\)\.

  **Required:** Conditional, based on other `Configuration` elements that are attached to the resource group\. This parameter is required only when the resource group also has another `Configuration` element with the `Type` of `AWS::EC2::HostManagement`\.

  The following example enables delete protection for the group unless the group has no members\.

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "deletion-protection",
                      "Values": [ "UNLESS_EMPTY" ]
                  }
              ]
          }
      ]
  }
  ```

### `AWS::AppRegistry::Application`<a name="about-slg-types-appregistry"></a>

This `Configuration` type specifies that the resource group represents an application created by AWS Service Catalog AppRegistry\.

Resource groups of this type are fully managed by the AppRegistry service, and can't be created, updated, or deleted by users other than by using the tools provided by AppRegistry\.

**Note**  
Because resource groups of this type are automatically created and maintained by AWS and not managed by the user, these resource groups do not count against your quota limit for the [maximum number of resource groups that you can create in your AWS account](https://console.aws.amazon.com/servicequotas/home/services/resource-groups/quotas)\.

For more information, see [Using AppRegistry](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/appregistry.html) in the *Service Catalog User Guide*\.

When AppRegistry creates a service\-linked resource group of this type, it also automatically creates a separate, additional [AWS CloudFormation service\-linked group](#about-slg-types-cloudformation) for each AWS CloudFormation stack associated with the application\.

AppRegistry automatically names the service\-linked groups of this type that its creates with the prefix `AWS_AppRegistry_Application-` followed by the name of the application: `AWS_AppRegistry_Application-MyAppName`

The following parameters are supported for the `AWS::AppRegistry::Application` service\-linked group type\.
+ **`Name`**

  This parameter specifies the friendly name of the application that was assigned by the user when it was created in AppRegistry\.

  **Data type of values:** String

  **Permitted values:** any text string permitted by the AppRegistry service for an application name\.

  **Required:** Yes
+ **`Arn`**

  This parameter specifies the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) path of the application assigned by AppRegistry\.

  **Data type of values:** String

  **Permitted values:** a valid ARN\.

  **Required:** Yes

**Note**  
To change any of these elements, you must modify the application using the AppRegistry console or that service's AWS SDK and AWS CLI operations\.

This application resource group automatically includes as group members the [resource groups created for the AWS CloudFormation stacks](#about-slg-types-cloudformation) that are associated with the AppRegistry application\. You can use the [ListGroupResources](https://docs.aws.amazon.com/ARG/latest/APIReference/API_ListGroupResources.html) operation to see those child groups\.

The following example shows what the configuration section of a `AWS::AppRegistry::Application` service\-linked group looks like\.

```
{
    "Configuration": [
        {
            "Type": "AWS::AppRegistry::Application",
            "Parameters":[
                {
                    "Name": "Name",
                    "Values": [
                        "MyApplication"
                    ]
                },
                {
                    "Name": "Arn",
                    "Values": [
                        "arn:aws:servicecatalog:us-east-1:123456789012:/applications/<application-id>"
                    ]
                }
            ]
        }
    ]
}
```

### `AWS::CloudFormation::Stack`<a name="about-slg-types-cloudformation"></a>

This `Configuration` type specifies that the group represents an AWS CloudFormation stack and its members are the AWS resources created by that stack\.

Resource groups of this type are automatically created for you when you associate a AWS CloudFormation stack with the AppRegistry service\. You can't create, update, or delete these groups except by using the tools provided by AppRegistry\.

AppRegistry automatically names the service\-linked groups of this type that its creates with the prefix `AWS_CloudFormation_Stack-` followed by the name of the stack: `AWS_CloudFormation_Stack-MyStackName`

**Note**  
Because resource groups of this type are automatically created and maintained by AWS and not managed by the user, these resource groups do not count against your quota limit for the [maximum number of resource groups that you can create in your AWS account](https://console.aws.amazon.com/servicequotas/home/services/resource-groups/quotas)\.

For more information, see [Using AppRegistry](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/AppRegistry.html) in the *Service Catalog User Guide*\.

AppRegistry automatically creates a service\-linked resource group of this type for every AWS CloudFormation stack that you associate with the AppRegistry application\. These resource groups become child members of the parent [resource group for the AppRegistry application](#about-slg-types-appregistry)\.

The members of this AWS CloudFormation resource group are the AWS resources created as part of the stack\.

The following parameters are supported for the `AWS::CloudFormation::Stack` service\-linked group type\.
+ **`Name`**

  This parameter specifies the friendly name of the AWS CloudFormation stack assigned by the user when the stack was created\.

  **Data type of values:** String

  **Permitted values:** any text string permitted by the AWS CloudFormation service for a stack name\.

  **Required:** Yes
+ **`Arn`**

  This parameter specifies the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) path of the AWS CloudFormation stack attached to the application in AppRegistry\.

  **Data type of values:** String

  **Permitted values:** a valid ARN\.

  **Required:** Yes

**Note**  
To change any of these elements, you must modify the application using the AppRegistry console or equivalent AWS SDK and AWS CLI operations\.

The following example shows what the configuration section of an `AWS::CloudFormation::Stack` service\-linked group looks like\.

```
{
    "Configuration": [
        {
            "Type": "AWS::CloudFormation::Stack",
            "Parameters":[
                {
                    "Name": "Name",
                    "Values": [
                        "MyStack"
                    ]
                },
                {
                    "Name": "Arn",
                    "Values": [
                        "arn:aws:cloudformation:us-east-1:123456789012:stack/MyStack/<stack-id>"
                    ]
                }
            ]               
        }
    ]
}
```

### `AWS::EC2::CapacityReservationPool`<a name="about-slg-types-ec2-capacityreservation"></a>

This `Configuration` type specifies that the resource group represents a common pool of capacity provided by the group's members\. The members of this resource group are required to be Amazon EC2 capacity reservations\. A resource group can include both capacity reservations that you own in your account and capacity reservations that are shared with you from other accounts by using AWS Resource Access Manager\. This lets you launch an Amazon EC2 instance using this resource group as the value for the capacity reservation parameter\. When you do this, the instance uses the available reserved capacity in the group\. If resource group has no available capacity, the instance launches as a stand alone on\-demand instance outside of the pool\. For more information, see [Working with Capacity Reservation groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/capacity-reservations-using.html#create-cr-group) in the *Amazon EC2 User Guide for Linux Instances*\.

If you configure a service\-linked resource group with a `Configuration` item of this type, then you must also specify separate `Configuration` items with the following values:
+ An `AWS::ResourceGroups::Generic` type with one parameter:
  + The parameter `allowed-resource-types` and a single value of `AWS::EC2::CapacityReservation`\. This ensures that only Amazon EC2 capacity reservations can be members of the resource group\.

The `AWS::EC2::CapacityReservationPool` item in a group configuration doesn't support any parameters\.

The following example shows what the `Configuration` section of such a group looks like\.

```
{
    "Configuration": [
        {
            "Type": "AWS::EC2::CapacityReservationPool"
        },
        {
            "Type": "AWS::ResourceGroups::Generic",
            "Parameters": [
                {
                    "Name": "allowed-resource-types",
                    "Values": [ "AWS::EC2::CapacityReservation" ]
                }
            ]
        }
    ]
}
```

### `AWS::EC2::HostManagement`<a name="about-slg-types-resourcegroups-ec2-hostmanagement"></a>

This identifier specifies settings for Amazon EC2 host management and AWS License Manager that are enforced for the group's members\. For more information, see [Host resource groups in AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/userguide/host-resource-groups.html)\.

If you configure a service\-linked resource group with a `Configuration` item of this type, then you must also specify separate `Configuration` items with the following values:
+ An `AWS::ResourceGroups::Generic` type, with a parameter of `allowed-resource-types` and a single value of `AWS::EC2::Host`\. This ensures that only Amazon EC2 dedicated hosts can be members of the group\. 
+ An `AWS::ResourceGroups::Generic` type, with a parameter of `deletion-protection` and a single value of `UNLESS_EMPTY`\. This ensures that the group can't be deleted unless the group is empty\.

The following parameters are supported for the `AWS::EC2::HostManagement` service\-linked group type\.
+ **`auto-allocate-host`**

  This parameter specifies whether instances are launched onto a specific dedicated host, or onto any available host that has a matching configuration\. For more information, see [Understanding auto\-placement and affinity](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-dedicated-hosts-work.html#dedicated-hosts-understanding) in the *Amazon EC2 User Guide for Linux Instances*\.

  **Data type of values:** Boolean

  **Permitted values:** "true" or "false" \(must be lower case\)\.

  **Required:** No

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::EC2::HostManagement",
              "Parameters": [
                  {
                      "Name": "auto-allocate-host",
                      "Values": [ "true" ]
                  }
              ]
          },
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": [ "AWS::EC2::Host" ]
                  },
                  {
                      "Name": "deletion-protection",
                      "Values": [ "UNLESS_EMPTY" ]
                  }
              ]
          }
      ]
  }
  ```
+ **`auto-release-host`**

  This parameter specifies whether a dedicated host in the group is automatically released after its last running instance is terminated\. For more information, see [Releasing Dedicated Hosts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-dedicated-hosts-work.html#dedicated-hosts-releasing) in the *Amazon EC2 User Guide for Linux Instances*\.

  **Data type of values:** Boolean

  **Permitted values:** "true" or "false" \(must be lower case\)\.

  **Required:** No

  ```
  {
      "Configuration": [ 
          {
              "Type": "AWS::EC2::HostManagement",
              "Parameters": [
                  {
                      "Name": "auto-release-host",
                      "Values": [ "false" ]
                  }
              ]
          },
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": [ "AWS::EC2::Host" ]
                  },
                  {
                      "Name": "deletion-protection",
                      "Values": [ "UNLESS_EMPTY" ]
                  }
              ]
          }
      ]
  }
  ```
+ **`allowed-host-families`**

  This parameter specifies which instance type families can be used by instances that are members of this group\.

  **Data type of values:** An array of String\. 

  **Permitted values:** Each must be a valid [Amazon EC2 instance type family identifier](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html#AvailableInstanceTypes), such as `C4`, `M5`, `P3dn`, or `R5d`\.

  **Required:** No

  The following example configuration item specifies that launched instances can be only members of the C5 or M5 instance type families\.

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::EC2::HostManagement",
              "Parameters": [
                  {
                      "Name": "allowed-host-families",
                      "Values": ["c5", "m5"]
                  }
              ]
          },
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": ["AWS::EC2::Host"]
                  },
                  {
                      "Name": "deletion-protection",
                      "Values": ["UNLESS_EMPTY"]
                  }
              ]
          }
      ]
  }
  ```
+ **`allowed-host-based-license-configurations`**

  This parameter specifies the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) paths of one or more core/socket based license configurations that you want applied to members of the group\.

  **Data type of values:** An array of ARNs\. 

  **Permitted values:** Each must be a valid [License Manager configuration ARN](https://docs.aws.amazon.com/service-authorization/latest/reference/about-service-linked-groups.xmllist_awslicensemanager.html#awslicensemanager-resources-for-iam-policies)\.

  **Required:** Conditional\. You must specify either this parameter or `any-host-based-license-configuration`, but not both\. They are mutually exclusive\.

  The following example configuration item specifies that group members can use the two specified License Manager configurations\.

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::EC2::HostManagement",
              "Parameters": [
                  {
                      "Name": "allowed-host-based-license-configurations",
                      "Values": [
                          "arn:aws:license-manager:us-west-2:123456789012:license-configuration:lic-6eb6586f508a786a2ba41EXAMPLE1111", 
                          "arn:aws:license-manager:us-west-2:123456789012:license-configuration:lic-8a786a26f50ba416eb658EXAMPLE2222"
                      ]
                  }
              ]
          },
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": [ "AWS::EC2::Host" ]
                  },
                  {
                      "Name": "deletion-protection",
                      "Values": [ "UNLESS_EMPTY" ]
                  }
              ]
          }
      ]
  }
  ```
+ **`any-host-based-license-configuration`**

  This parameter specifies that you do not want to associate a specific license configuration to your group\. In this case, all core/socket based license configurations are available to your members of your host resource group\. Use this setting if you have an unlimited number of licenses and want to optimize for host utilization\.

  **Data type of values:** Boolean

  **Permitted values:** "true" or "false" \(must be lower case\)\.

  **Required:** Conditional\. You must specify either this parameter or `allowed-host-based-license-configurations`, but not both\. They are mutually exclusive\.

  The following example configuration item specifies that group members can use any core/socket based license configuration\.

  ```
  {
      "Configuration": [
          {
              "Type": "AWS::EC2::HostManagement",
              "Parameters": [
                  {
                      "Name": "any-host-based-license-configuration",
                      "Values": ["true"]
                  }
              ]
          },
          {
              "Type": "AWS::ResourceGroups::Generic",
              "Parameters": [
                  {
                      "Name": "allowed-resource-types",
                      "Values": ["AWS::EC2::Host"]
                  },
                  {
                      "Name": "deletion-protection",
                      "Values": ["UNLESS_EMPTY"]
                  }
              ]
          }
      ]
  }
  ```

The following example illustrates how to include all of the host management settings together in a single configuration\.

```
{
    "Configuration": [
        {
            "Type": "AWS::EC2::HostManagement",
            "Parameters": [
                {
                    "Name": "auto-allocate-host",
                    "Values": ["true"]
                },
                {
                    "Name": "auto-release-host",
                    "Values": ["false"]
                },
                {
                    "Name": "allowed-host-families",
                    "Values": ["c5", "m5"]
                },
                {
                    "Name": "allowed-host-based-license-configurations",
                    "Values": [
                        "arn:aws:license-manager:us-west-2:123456789012:license-configuration:lic-6eb6586f508a786a2ba41EXAMPLE1111",
                        "arn:aws:license-manager:us-west-2:123456789012:license-configuration:lic-8a786a26f50ba416eb658EXAMPLE2222"
                    ]
                }
            ]
        },
        {
            "Type": "AWS::ResourceGroups::Generic",
            "Parameters": [
                {
                    "Name": "allowed-resource-types",
                    "Values": ["AWS::EC2::Host"]
                },
                {
                    "Name": "deletion-protection",
                    "Values": ["UNLESS_EMPTY"]
                }
            ]
        }
    ]
}
```

### `AWS::NetworkFirewall::RuleGroup`<a name="about-slg-types-network-firewall-rulegroup"></a>

This identifier specifies settings for AWS Network Firewall rule groups that are enforced for the group's members\. Firewall administrators can specify the ARN of a resource group of this type to automatically resolve the IP addresses of the group's members for a firewall rule instead of having to list each address manually\. For more information, see [Using tag\-based resource groups in AWS Network Firewall](https://docs.aws.amazon.com/network-firewall/latest/developerguide/resource-groups.html)\.

You can create resource groups of this configuration type by using the Network Firewall console or by running a AWS CLI command or AWS SDK operation\.

Resource groups of this configuration type have the following restrictions:
+ The group's members consist of only resources of types supported by Network Firewall\.
+ The group must contain a tag\-based query to manage the group's membership; any resources of supported types with tags that match the query are automatically members of the group\.
+ There are no `Parameters` supported for this configuration type\. 
+ To delete a resource group of this configuration type, it can't be referenced by any Network Firewall rule group\.

The following example illustrates the `Configuration` and `ResourceQuery` sections for a group of this type\.

```
{
    "Configuration": [
        {
            "Type": "AWS::NetworkFirewall::RuleGroup",
            "Parameters": []
        }
    ],
    "ResourceQuery": { 
        "Query": "{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"environment\",\"Values\":[\"production\"]}]}",
        "Type": "TAG_FILTERS_1_0"
    }
}
```

The following example AWS CLI command creates a resource group with the previous configuration and query\.

```
$ aws resource-groups create-group \
    --name test-group \
    --resource-query '{"Type": "TAG_FILTERS_1_0", "Query": "{\"ResourceTypeFilters\": [\"AWS::EC2::Instance\"], \"TagFilters\": [{\"Key\": \"environment\", \"Values\": [\"production\"]}]}"}' \
    --configuration '[{"Type": "AWS::NetworkFirewall::RuleGroup", "Parameters": []}]'
{
    "Group":{
        "GroupArn":"arn:aws:resource-groups:us-west-2:123456789012:group/test-group",
        "Name":"test-group",
        "OwnerId":"123456789012"
    },
    "Configuration": [
        {
            "Type": "AWS::NetworkFirewall::RuleGroup",
            "Parameters": []
        }
    ],
    "ResourceQuery": { 
        "Query": "{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"environment\",\"Values\":[\"production\"]}]}",
        "Type": "TAG_FILTERS_1_0"
    }
}
```