# Scenario: Implementing a New Tagging Strategy<a name="scenario-implementing-tagging"></a>

Consider a situation where you have a medium to large working environment with multiple resources used by various employees\. You decide to use tagging to help you organize and get better oversight of your account’s resources\. But how to proceed when there are dozens of resources to tag? Fortunately, Tag Editor can simplify the process\.

1. **Make a plan\.**

   Before you begin, sketch out a plan of the tag keys and values that will help you organize your resources\. For example, you might want all resources to have tag keys like *Project*, *Cost Center*, and *Environment*\. Remember, too, that each resource cannot have more than 50 tags\.

1. **Open Tag Editor\.**

   Sign into the AWS Management Console and open Tag Editor at [https://resources\.console\.aws\.amazon\.com/r/tags](https://resources.console.aws.amazon.com/r/tags)\.

1. **Find all resources in your account\.**

   For **Regions**, select all regions that apply\. For **Resource types**, select **All resource types**\. Leave both **Tags** boxes empty\. Then choose **Find resources**\. For more information, see [Searching for Resources to Tag](searching-resources-to-tag.md)\.

1. **Select all the found resources\.**

   The Tag Editor search results appear at the bottom of the page\. When the list shows the resources that you want to tag, select the top check box to select all resources\. Choose **Edit tags for selected**\.

1. **Apply tag keys with empty elements\.**

   In **Add/edit tags**, under **Add tags**, in the space provided, type the key name that you want to add, such as **Project**\. Repeat for your other new keys, such as **Cost Center** and **Environment**\. Choose **Apply changes**\.
**Tip**  
If any of your selected resources have reached the maximum of 50 tags, a message warns you before you choose **Apply changes**\. You can pause the pointer over the number of affected resources in the message to see a pop\-up list of the specific resources\.

1. **Add values for each tag key\.**

   The next step is to add tag values that will help you distinguish individual resources that share tag keys\. There are a couple of ways to do this depending on whether you plan on adding the same values to many resources or just a few\.

   1. **Bulk add values\.**

      Start by selecting the check box at the top of the table again to clear all the check boxes\. Then select individual check boxes for just those resources that need a specific tag value\.

      Choose **Edit tags for selected**\. In **Add/edit tags**, under **Applied tags**, type a new value in the **Value** column next to a tag key\. For example, you might add a billing code in the value for the Cost Center key or type **Production** for the Environment key\.

      Note that if the **Value** column shows **Multiple values**, you can still type in a new value\. However, your new value will replace all the key’s existing values for the selected resources\.

      When you’re done, choose **Apply changes**\.

   1. **Add individual tag values\.**

      If you want each resource to have its own unique value, you can edit tag values right in the search results table\. Start by choosing the cog icon above the table and selecting the check boxes for your new keys\. To continue our example, you might select the check boxes for **Project**, **Cost Center**, and **Environment**\. This makes your keys appear as columns in the search results table\.

      For a given resource, locate the column that displays the tag key whose value you want to edit\. Choose the pencil icon, and then type the new value in the box\. Press **Enter** to complete the editing\.

1. **Repeat [[ERROR] BAD/MISSING LINK TEXT](#add-values-for-each-tag-key) for other resources in your list\.**