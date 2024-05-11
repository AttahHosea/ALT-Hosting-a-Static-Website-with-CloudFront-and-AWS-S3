# Hosting-a-Static-Website-with-CloudFront-and-AWS-S3

## Task
Create a static website and host it on S3 bucket(private bucket) but with public read policy assigned, using cloud front for CDN

## Requirements

i. An AWS account
ii. Webpage or website files for hosting (HTML, CSS, JS, etc)

## Steps 

### Create a Bucket on Amazon S3

i. After sign up and registration on AWS, Log into your AWS console and search for **S3** and click on it.

ii. Next, click on **create bucket**, go ahead to fill in a unique bucket name that has not been used, untick **Block all public access** and acknowledge the box below it.

![S3](https://asset.cloudinary.com/dbzdpfq9c/f82a838b6b7723c42332fbf955081ef9) ![public access](https://asset.cloudinary.com/dbzdpfq9c/8cf8e465af6a72bc83d4eda0bb069a94)

iii. Leave all other settings unchecked and scroll down to click **create bucket**.

![bucket success](https://asset.cloudinary.com/dbzdpfq9c/e0d19ac5a3f396e03abf12b5d1ea092c)

### Upload Website files to S3 Bucket

i. Click on the bucket name you created.

ii. On the next screen, click on **upload** and select the files from your local computer. **NOTE:** Don't try to upload everything at once in a single folder. Instead, upload your files based on their type; if you have a folder containing images, a folder for css and an index.html file, upload the two folders first by clicking **upload folder** and selecting them, this will upload both files individually with their structures, then click **upload file** and select index.html.

![upload](https://res.cloudinary.com/dbzdpfq9c/image/upload/v1715415414/ALT/four_k6dwk8.png)

iii. Click on **Add folders** or **Add file** and upload your folders and files.

![upload folders](https://asset.cloudinary.com/dbzdpfq9c/9bfe99ecaacc43fd10ed1f80da1c0c95)

iv. After uploading the folders from your computer, click on **Upload**. Wait for the process to complete with a success banner at the top.

![upload success](https://asset.cloudinary.com/dbzdpfq9c/941162848f312de0173a8bca1da0a55e)

### Enable Static Website Hosting on S3 Bucket Created

i. After uploading, inside the S3 bucket click on the **Properties** tab and scroll down to **Static website hosting**

![Static website hosting](https://asset.cloudinary.com/dbzdpfq9c/98b49a37e3583af21c477629bc8c40f0)

ii. Click **Edit** on **Static website hosting** and select **Enable**.

![edit static](https://asset.cloudinary.com/dbzdpfq9c/57b4da299f3080daf6ec941738a94912)

iii. Select **Host a static website** under **hosting type**. Under **Index document**, type "index.html" in it.

![Static settings](https://asset.cloudinary.com/dbzdpfq9c/125607c2f15ac98c0fc4a06a882bdff8)

iv. Leave other settings as default and **save changes** at the bottom.

![static success](https://asset.cloudinary.com/dbzdpfq9c/d3d07c0562c46c3f974a7d389172010d)

### Attach a Bucket Policy

i. Click on **Permissions** tab, scroll down to **Bucket policy** and click on **Edit**

ii. Input the policy attached below. Scroll down and click on **save changes**. **NOTE:** Replace "wp-pusher" with your own bucket name.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::wp-pusher/*"
        }
    ]
}
```

![policy](https://asset.cloudinary.com/dbzdpfq9c/a894080b65f67c3b7b18d1a13b5e4999)
![policy success](https://asset.cloudinary.com/dbzdpfq9c/1a566f38105bfd1856d42b4d068b32ac)


iii. Click on the **Properties** tab and scroll down to **Static website hosting**, click on the link and your static website should upen in the next tab in your browser.

![image](https://asset.cloudinary.com/dbzdpfq9c/ae830f2628d9c0cec9f012fd7c5726ee)
![image](https://asset.cloudinary.com/dbzdpfq9c/ae830f2628d9c0cec9f012fd7c5726ee)