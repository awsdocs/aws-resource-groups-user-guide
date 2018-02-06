# Finding Untagged Resources<a name="scenario-finding-untagged"></a>

You might find it useful to know what resources in your account have yet to be tagged\. You might also want to know what resources have tag keys but no tag values\. You can use Tag Editor to find these resources\.

1. Sign into the AWS Management Console and open Tag Editor at [https://resources\.console\.aws\.amazon\.com/r/tags](https://resources.console.aws.amazon.com/r/tags)\.

1. For **Regions**, select the regions that you want to include\.

1. For **Resource types**, select the resource types that you want to search for\.

1. For **Tags**, select a tag key that you want to apply to resources that do not already have it\.

1. In the next box, do either or both of the following, depending on your goal:

   + Choose **Not tagged** to find resources with no specified tags\. 

      

   + Choose **Empty value** to find resources that are tagged with your specified key but that have no tag value\.

1. Choose **Find Resources** to have Tag Editor find all such resources and list them at the bottom of the page\.

1. \(Optional\) Use any of the methods discussed in [Tagging Resources](tagging-resources.md) to add tags to the resources in the search results\.