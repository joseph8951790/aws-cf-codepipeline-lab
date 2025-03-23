# AWS Automated CI/CD Pipeline with CloudFormation and CodePipeline

## Objective

The objective of this project is to set up an automated Continuous Integration/Continuous Deployment (CI/CD) pipeline using AWS CodePipeline to provision AWS resources with CloudFormation.

---

## Project Structure

```
aws-cf-codepipeline-lab/
├── s3_bucket.yaml
└── README.md
```

---

## Steps to Complete the Lab

### Step 1: CloudFormation Template
- Created a CloudFormation YAML template (`s3_bucket.yaml`) to provision an S3 bucket.
- Included parameters for `BucketName` and `VersioningStatus`.
- Validated the template locally:
  ```bash
  aws cloudformation validate-template --template-body file://s3_bucket.yaml
  ```

### Step 2: Set Up GitHub Repository
- Created a GitHub repository named `aws-cf-codepipeline-lab`.
- Uploaded the CloudFormation template to the `main` branch.

### Step 3: Configure AWS CodePipeline
- Set Source stage to the GitHub repository (`main` branch).
- Configured Deploy stage with AWS CloudFormation:
  - Stack Name: `AutomatedS3Bucket`
  - Template file: `s3_bucket.yaml`
  - Parameter overrides:
    ```
    BucketName=josephcicd45637-bucket,VersioningStatus=Enabled
    ```

### Step 4: Automated Deployment
- Enabled automatic deployment triggers on pushes to the repository.
- Tested the pipeline by modifying the template and pushing changes.

### Step 5: Verify and Clean Up
- Verified successful creation of the S3 bucket in AWS Console.
- Deleted the CloudFormation stack after testing to avoid AWS charges:
  ```
  aws cloudformation delete-stack --stack-name AutomatedS3Bucket
  ```

---

## Screenshots and Logs

- Provided screenshots of:
  - CodePipeline stages and successful execution.
  - Deployed AWS resources (S3 bucket).
  - CloudFormation stack status (`CREATE_COMPLETE`).

---

## Author

**Joseph Johnson Vettamvely**  
**Student ID:** 8951790


