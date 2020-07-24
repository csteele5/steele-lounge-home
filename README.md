# SteeleLounge Home

## Summary
This is the entry point for all Internet facing resources made public for demo purposes or personal use.

## Design Notes
The landing site is hosted on S3 as a static web page with links to other AWS resources as needed.  To minimize S3 bucket usage, reference links to external resources will be used when practical.

**S3 >> Cloudfront >> Certificate Manager >> Route53**
Initial setup involved connecting a single S3 bucket with all web files to multiple cloudfront distributions to cover steelelounge.com, www.steelelounge.com, and home.steelelounge.com.  This was successfully setup with SSL using Certificate Manager, but the file updating process was painful.  The cache would not instantly update (24/12 hour latency).  This approach was abandoned in favor of direct S3 to Route 53 without SSL

**S3 >> Route53**
Route53 recordsets for both steelelounge.com and www.steelelounge.com are set up without SSL, directly to 2 buckets. steelelounge.com has all of the files and www.steelelounge.com is set up as a redirect to the other.

## Resources
Template used - [Bootstrap Resume Theme](https://startbootstrap.com/themes/resume/)
Bootstrap documentation - [Bootstrap 4](https://getbootstrap.com/)
Hooking up S3, Cloudfront, and Route53 [AWS for Newbs](https://awsnewbies.com/s3-website-route-53-cloudfront/)
Linking S3 Directly to Route59 [AWS Route53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started.html#getting-started-create-s3-www-bucket)