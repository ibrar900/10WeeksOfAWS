# Week 1 Submission - Ibrar Mahammad
..........

## Name
..........
Ibrar Mahammad



## Tasks Completed
- read the weekly content and watched all the AWS console menu and options and searchbar.
- Completed all hands-on labs
- Added screenshots for all the labs
- Deleted the lab resources to avoid costs
- Posted on Linkedin.

## What I Built
- AWS Account Sign-up and add MFA Authnticator app for security.
- Created IAM user with Admin access and added MFA Authnticator app for security.
- Do not use root account for daily work.
- created billing alert and CloudWatch alarm , SNS topic and added billing alert for $5 and email to my mail for billing alerts. 
- Created IAM User, Group,Policy and Role and attached policies to groups and users.
- Practiced how to create groups and users and add them to groups and apply policies to groups and users.
- Created s3 bucket and uploaded content and observed how policy will effect and control for users and groups.
- created custom policy for s3 and attached to user and group.
- created role for ec2 and attached to s3.
- hands on experience how IAM switch role works and gives temporary credentials to a trusted identity.
- learned how GitHub Actions accessing AWS using OIDC and AWS STS without access keys.

## LinkedIn Post
................
https://www.linkedin.com/posts/ibrar-mahammad-58489b26a_100daysofcloud-aws-iam-activity-9261942601667964928-uF_9?utm_source=share&utm_medium=member_desktop

## Topics Practiced
...........
- AWS account 
- Root amd IAM MFA for security
- IAM Users
- IAM Groups 
- IAM Roles and OIDC temporary access
- IAM Policies
- JSON Policy
- Least privilege
- GitHub OIDC based temporary access
- IAM Switch role
- Custom JSON file policy
- Billing alert
- Optional GitHub OIDC

## What I Learned
Today I learned how IAM controls access in AWS.

Identity + Permissions = Access.

## Where I Got Stuck
Write one problem you faced. If everything worked, write "No blocker".

## Screenshots Added
- Root MFA
- Billing alert
- IAM group
- IAM user
- Access allowed
- Access denied

## Key Takeaway
Least privilege means giving only required permissions, nothing extra.

LAB 1 - Secure Your AWS Account
...............
Goal: Create a safe AWS account foundation for the next 10 weeks.

Steps:

1. Create and Login into AWS Root account.
2. add MFA to root account 
3. Create IAM user with admin access
4. add MFA to IAM user
5. Create billing alert for $5
6. Stop using root account for daily work.

before Creating an AWS Billing Alarm, make sure these prerequisites are met:

1.Enable Billing Alert

- Sign in as root user or IAM User with Admin access
- Open the Billing and Cost management console
- In the navigation pane, choose Cost Explorer.
- Choose Create a cost budget.
- Go to Billing preferences->Cost usage reports->Activate Cost Explorer.
- Enable Receive CloudWatch billing alerts.

2.UUse the North Virginia(us-east-1) AWS Region

- Billing metrics are available only in US East (N. Virginia) (us-east-1).
-Create the alarm in this region.

Deliverables:

Root MFA enabled
![alt text](<Root MFA enabled-2.png>)

Billing Alert
![alt text](<Bill and Cost Management Monthly.png>)

![alt text](<CloudWatch Alarm.png>)

Budget Alert
![alt text](<Monthly Cost Budget .png>)

Where i Got Struck
..................................

Cloud watch Alert, Billing Alert, Budget Alert differences. how they work and how to create them.

## Lab 2 — S3 Read-Only IAM Group and User
Goal: Understand IAM group-based access.

Create group:

Group name: S3ReadOnlyGroup
Policy: AmazonS3ReadOnlyAccess

Create user:

User name: learner-s3
Add user to: S3ReadOnlyGroup

Test:

1.Log in as learner-s3.
2.Open S3.
3.Confirm you can view/list S3 buckets.
4.Try an action that is not allowed.
5.Observe Access Denied.

Deliverables:

Group created & Policy Attached

![alt text](<Screenshot of S3group created.png>)

User Added to group

![alt text](<Screenshot of S3 policy attached.png>)

Allowed S3 view action

![alt text](<Screenshot of allowed S3 view action.png>)

![alt text](<Screenshot of denied action S3.png>)

## Lab 3 — EC2 Read-Only Access
Goal: Apply least privilege to EC2.

Create group:

Group name: EC2ReadOnlyGroup
Policy: AmazonEC2ReadOnlyAccess

Create user:

User name: learner-ec2
Add user to: EC2ReadOnlyGroup

Test:

1.Log in as learner-ec2.
2.Open EC2 dashboard.
3.Confirm EC2 resources are visible.
Confirm the user cannot create or terminate instances.

Deliverables:

EC2ReadOnlyGroup & Policy attached

![alt text](<Screenshot of EC2ReadOnlyGroup.png>)

User Added to group

![alt text](<Screenshot of EC2 policy attached.png>)

EC2 Dashboard access

![alt text](<Screenshot or note for denied create-terminate action.png>)

Denied Terminate action

![alt text](<Screenshot of EC2 dashboard access.png>)

## Lab 4 — Billing View Access
Goal: Understand billing access with limited permissions.

Create group:

Group name: BillingViewGroup
Policy: AWSBillingReadOnlyAccess

Create user:

User name: learner-billing
Add user to: BillingViewGroup

Test:

Log in as learner-billing.
Open Billing Dashboard.
Verify billing visibility.
Confirm user cannot manage unrelated AWS services.

Deliverables:

BillingViewGroup & Policy attached

![alt text](<Screenshot of BillingViewGroup.png>)

Billing Dashboard access

![alt text](<Screenshot of Billing Dashboard access.png>)

learner-billing user cannot manage unrelated AWS services

![alt text](<Screenshot of denied action S3-1.png>)

## Lab 5 — Custom S3 Read-Only JSON Policy
Goal: Read and create a basic JSON policy.

Create a customer managed policy:

Policy name: CustomS3ReadOnlyTrainingPolicy

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListAllMyBuckets",
        "s3:GetBucketLocation"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}

Deliverables:

Custom S3 Policy
CustomS3ReadOnlyTrainingPolicy

Custom Policy Created

![alt text](<Custom Policy Created.png>)

Policy Attached to learner-s3 user

![alt text](<Policy Attached to learner-s3 user.png>)

uccessfully listed all S3 buckets
Successfully viewed objects in ibrar-s3-bucket.
Successfully downloaded resume.pdf








