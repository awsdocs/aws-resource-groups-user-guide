# Working with Tag Editor<a name="tag-editor"></a>

Tags are words or phrases that act as metadata for identifying and organizing your AWS resources\. The tag limit varies with the resource, but most can have up to 50 tags\. Each tag consists of a key and a value\. For more about tagging, see [Using Cost Allocation Tags](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html#allocation-what) in the *AWS Billing and Cost Management User Guide*\.

You can add tags to resources when you create the resource or add, change, or remove those tags one resource at a time within each resource’s console\. To add to multiple resources at once, you need to use Tag Editor\. With Tag Editor, you search for the resources that you want to tag, and then add, remove, or edit tags for the resources in your search results\.

**To start Tag Editor**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/console/home)\.

1. On the navigation bar, choose **Resource Groups**, and then choose **Tag Editor**\.

Not all resources can have tags applied\. To see if a resource supports tagging, consult the documentation for that resource's service\.

For information about permissions and roles that are required to tag resources, see \.


+ [Searching for Resources to Tag](searching-resources-to-tag.md)
+ [Finding Untagged Resources](scenario-finding-untagged.md)
+ [Customizing Tag Search Results](customizing-tag-search-results.md)
+ [Tagging Resources](tagging-resources.md)
+ [Scenario: Implementing a New Tagging Strategy](scenario-implementing-tagging.md)