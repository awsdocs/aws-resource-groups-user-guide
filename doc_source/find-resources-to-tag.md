# Find resources to tag<a name="find-resources-to-tag"></a>

With Tag Editor, you build a query to find resources in one or more AWS Regions that are available for tagging\. You can choose up to 20 individual resource types, or build a query on **All resource types**\. Your query can include resources that already have tags, or resources that have no tags\. For more information, see [Resource types you can use with AWS Resource Groups and Tag Editor](supported-resources.md)\.

After you find resources to tag, you can use Tag Editor to add tags, or view, edit, or delete tags\.

**To find resources to tag**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/resource-groups), choose **Resource Groups**, and then choose **Tag Editor**\.

1. *\(optional\)* Choose regions in which to search for resources to tag\. By default, your current region is selected\. For this walkthrough, choose **us\-east\-1** and **us\-west\-2**\.  
![\[Find resources to tag page with us-east-1 and us-west-2 selected as regions.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_findresources_regions.png)

1. Choose at least one resource type from the **Resource type** drop\-down list\. You can add or edit tags for up to 20 individual resource types at a time, or choose **All resource types**\. For this walkthrough, choose **AWS::EC2::Instance** and **AWS::S3::Bucket**\.  
![\[Find resources to tag page with EC2 instances and S3 buckets selected as the resource type.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_findresource.png)

1. *\(optional\)* In the **Tags** fields, enter a tag key, or a tag key and value pair, to limit the resources in the current AWS Region to only those that are tagged with your specified values\. As you type a tag key, matching tag keys in the current region appear in a list below; you can choose a tag key from the list\. Tag Editor auto\-completes the tag key for you as you type enough characters to match an existing key\. Choose **Add** or press **Enter** when you've finished your tag\. In this example, filter for resources that have a tag key of **Stage**\. The tag value is optional, but narrows the results of the query further\. To add more tags, choose **Add**\. Queries assign an `AND` operator to tags, so any resource that matches the specified resource type and all specified tags is returned by the query\.

   To find resources with multiple values for a tag key, add another tag with the same key to the query, but specify a different value\. The results include all resources that are tagged with the same tag key and that have any of the selected values\. The search is case sensitive\.

   Leave the **Tags** boxes empty to find all resources of the specified type in the current AWS Region\. This query returns resources that have any tags, and includes those that have no tags\. To remove a tag from your query, choose **X** on the tag's label\.

   To find resources that have an empty value for a tag, choose **\(empty value\)** when your cursor is in the tag value box\.   
![\[Find resources to tag page with empty value chosen as the tag value.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_findresource_emptyvalue.png)
**Note**  
Before you can find resources with the specified tags, they must have been applied to at least one resource of the specified type in the current AWS Region\.

1. When your query is ready, choose **Search resources**\. Results are displayed in the **Resource search results** area\.  
![\[Find resources query results.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_findresources_results.png)

   To filter a large number of resources, enter any filter text, such as part of the name of a resource, in **Filter resources**\.

1. *\(optional\)* To configure the columns that Tag Editor displays in your resource search results, choose the **Preferences** gear icon ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/gearicon.png) in the **Resource search results**\.

   On the **Preferences** page, choose the number of rows that you want displayed in your search results\.

   Turn on columns that you want Tag Editor to display in your results\. You can show a column for each tag that occurs in your search results or a selected subset of your search results\. You can do this any time after you find resources to tag\. To enable a column, choose the switch icon next to the tag and change it from off ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/switch-off.png) to on ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/switch-on.png)\.  
![\[Preferences page.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_findresources_preferences.png)

   When you are finished configuring visible columns and number of displayed rows, choose **Confirm**\.

## View and edit tags for a selected resource<a name="tagging-resources-view"></a>

Tag Editor shows you the existing tags on selected resources that are in the results of your **Find resources to tag** query\. 

If you enabled any of the **Tag** columns as described in the previous section, then you can see the current value of that tag for each resource in the search results\.

**Note**  
This topic explains how to edit the tag for an *individual* resource\. You can also bulk edit tags for several selected resources at the same time\. For more information, see [Manage tags](tagging-resources.md)\.

**To edit tags inline in the search results table**

1. Choose the value for the tag on the resource that you want to edit\. 
**Note**  
If the chosen resource currently does not have a tag with the chosen key, the value displays as **\(not tagged\)**\.
If the chosen resource does have a tag with the chosen key but without a value, the value displays as '**–**'\. 

   In the following example, the column for the tag **Env** and with the current value of **Prod** was chosen\.  
![\[Inline editing of a tag value.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te-inline-edit.png)

1. You can enter a new value or choose from any of the values already present on other resources with this tag\. You can also delete the tag from this one resource by choosing **Remove tag**\.

**To view all tags for an individual resource**

1. In the results of your **Find resources to tag** query, choose the number in the **Tags** column for any resource for which you want to view existing tags\. Resources with a dash in the **Tags** column do not have existing tags\.  
![\[Find resources query results with no resources selected.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_view_tags_query.png)

1. View existing tags in **Resource tags**\. You can also open this window on the **Manage tags** page, when you are changing or removing tags\.  
![\[Resource tags page.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_view_tags.png)
**Note**  
If you don’t see a tag that you recently applied to a resource, try refreshing your browser window\.

## Export Results to CSV<a name="tagging-resources-csv"></a>

You can export the results of a **Find resources to tag** query to a comma\-separated values \(CSV\) file\. The CSV file includes the resource names, services, region, resource IDs, the total number of tags, and a column for each unique tag key in the collection\. The CSV file can help you develop a tagging strategy for resources in your organization, or determine where there are overlaps or inconsistencies in tagging across resources\.

1. In the results of your **Find resources to tag** query, choose **Export resources to CSV**\.  
![\[Find resources query results with Export 8 resources to CSV command button shown.\]](http://docs.aws.amazon.com/ARG/latest/userguide/images/te_view_tags_query.png)

1. When you are prompted by your browser, choose to open the CSV file \(typically in Microsoft Excel\), or save it to a convenient location\.

## Related information<a name="related-info-finding-resources"></a>
+ [AWS Tagging Strategies](http://aws.amazon.com/answers/account-management/aws-tagging-strategies/)
+ [Using cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html#allocation-what)
+ [Tag Editor](tag-editor.md)