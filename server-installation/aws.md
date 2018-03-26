# AWS S3 document storage

AWS S3 document storage is use3d to store user uploaded documents, specifically used for attaching documents to progress updates

#### Sign up to Amazon Web Services (AWS)

[Sign up](https://portal.aws.amazon.com/billing/signup) for a free account and/or [log in](https://signin.aws.amazon.com/signin)

#### Set up S3 bucket

- go to S3
- create bucket
- enter bucket name and select region (e.g. US West (Oregon)) - remember region id (e.g. "us-west-2")
- set permissions: under "manage public permissions" select "Grant public access to this bucket"

#### Set up user

- go to IAM (Identity and Access Management)
- create new user group
- create group "inline policy" with bucket name (replace `bucket-name` with bucket name chosen), eg
  ```
  {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": [
                "arn:aws:s3:::bucket-name/*"
            ]
        }
    ]
  }
  ```
- create user (access type: "Programmatic access") and add to group
- create access key and/or remember "Access key ID" and "Secret access key"
