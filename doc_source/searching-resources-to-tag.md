# Searching for Resources to Tag<a name="searching-resources-to-tag"></a>

With Tag Editor, you can locate all the resources that are available for tagging\. For more information, see [Supported Resources for Tag Editor Tagging](supported-resources.md#supported-resources-tagging-console)\.

**To search for resources to tag**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/console/home), choose **Resource Groups**, and then choose **Tag Editor**\.

1. For **Regions**, choose the regions that you want to search in\. Repeat for as many regions as you want\. To remove a region, choose the **x** by its name\.

1. For **Resource types**, choose the kind of resources that you want to locate\. Repeat for as many resource types as you want\. To remove a region or resource type, choose the **x** by its name\. To search for all resource types or all regions, select **All resource types**\.

1. \(Optional\) To limit your search to resources that already have certain tag keys or values, in the first **Tags** box choose the name of a tag key\. Type in the box to search for a key based on characters that it contains\. 

1. \(Optional\) In the next **Tags** box, do any of the following:

   + Leave the box empty to search for all resources with the specified key and any value\.

      

   + Select **Not tagged** to search for resources that do *not* have the specified tag key\.

      

   + Select **Empty value** to search for resources that have the specified tag key but no value\.

      

   + Type one or more characters to find resources with the values that you are looking for\. Select a value from the list to find an exact match or select the **Contains:** option to find values that contain the characters that you typed\.

     If you don’t see any values listed, you might not have permissions to view available tags\. In that case, you can simply type in a complete value and press **Enter** to start searching\.

      

   + Choose the **x** next to an item that you added to remove it from the search criteria\. 

   You can add multiple values for each tag key\. Doing so potentially increases the number of resources in the search results because the results include resources tagged with any of the selected values\. The search is case sensitive\.
**Note**  
Before a key and its values appear in this list, they must have been applied to at least one resource in the current account\. If you don’t see a tag that you just applied to a resource, try refreshing your browser window\.

1. \(Optional\) To further refine your group, continue using the **Tags** boxes at the bottom to specify more tag keys and values\. The search results contain only those resources that have all the specified tags, so the more tags you specify, the fewer resources Tag Editor finds\.

1. When you have the settings that you want, choose **Find resources**\.