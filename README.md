# EX6

## Login into AWS and Implement Identity Management Using Amazon IAM
## Name: SWETHA R
## Reg No: 212225100055
## Aim

To create and configure IAM users and groups in AWS, assign permissions using IAM policies, enable console access, and verify role-based access to Amazon S3.

## Requirements

- AWS Account
- Internet connection
- Web browser
- Amazon S3 bucket

## Procedure

### Step 1: Login to AWS Management Console

1. Open a web browser.
2. Go to the AWS Management Console.
3. Sign in using the AWS account credentials.
4. Search for **IAM** using the AWS search bar.
5. Open **IAM (Identity and Access Management)**.

### Step 2: Create an IAM Group

1. In the IAM dashboard, select **User groups** from the left-side menu.
2. Click **Create group**.
3. Enter the group name:

   **cloudSecurity_2026**

4. Do not add users at this stage if the user will be created separately.
5. Click **Create user group**.

The group **cloudSecurity_2026** is now created.

### Step 3: Attach an IAM Policy to the Group

1. Open the **cloudSecurity_2026** group.
2. Select the **Permissions** tab.
3. Click **Add permissions**.
4. Select **Attach policies directly**.
5. Search for:

   **AmazonS3ReadOnlyAccess**

6. Select the checkbox for **AmazonS3ReadOnlyAccess**.
7. Click **Next** and then **Add permissions**.

The group now has read-only access to Amazon S3.

### Step 4: Create an IAM User

1. From the IAM navigation menu, select **Users**.
2. Click **Create user**.
3. Enter the username:

   **student01**

4. Click **Next**.

### Step 5: Add the User to the IAM Group

1. On the **Permissions** page, select **Add user to group**.
2. Select:

   **cloudSecurity_2026**

3. Click **Next**.
4. Review the configuration.
5. Click **Create user**.

The user is now a member of the **cloudSecurity_2026** group.

### Step 6: Verify User Permissions

1. Open **IAM → Users**.
2. Click **student01**.
3. Open the **Permissions** tab.
4. Verify that the following policy is displayed:

   **AmazonS3ReadOnlyAccess**

5. Check the **Attached via** column.
6. It should indicate that the policy is attached through:

   **Group: cloudSecurity_2026**

This demonstrates:

```
text
student01
    ↓
cloudSecurity_2026
    ↓
AmazonS3ReadOnlyAccess
    ↓
Amazon S3 Read-only Access
```

## Step 7: Enable Console Access

Initially, console access for student01 may be disabled.

Open IAM → Users → student01.
Select Security credentials.
Locate Console access / AWS Management Console access.
Enable console access.
Create a console password for student01.
Complete the configuration.

### Note: Do not share the password with other users.

## Step 8: Obtain the AWS Account ID

The IAM user login requires the AWS account ID.

Your AWS account ID is a 12-digit number.
It can be found in the AWS account information.
Students should use their own AWS account ID when performing the experiment.

### AWS Account ID: YOUR_AWS_ACCOUNT_ID

## Step 9: Login as the IAM User
Sign out from the current AWS administrator/root session.
Open a new browser window or Incognito/Private window.
Open the AWS sign-in page.
Select IAM user login.
Enter the AWS account ID.

Enter the IAM username:

student01

Enter the password created in Step 7.
Click Sign in.

The AWS Management Console should now open under the IAM user student01.

## Step 10: Verify Amazon S3 Access
After logging in as student01, search for S3.
Open Amazon S3.
Select General purpose buckets.
Verify that the previously created S3 bucket is visible.
Open the bucket.
Verify that the user can view the bucket and its objects.

This confirms that the IAM policy is providing S3 read access.

## Step 11: Verify Least-Privilege Access

The user student01 has been assigned:

AmazonS3ReadOnlyAccess

Therefore, the user should have read access but should not have permission to perform S3 write/delete operations.

### For testing:

Open the S3 bucket as student01.
Observe the available operations.
Do not delete any existing object.
If you test an upload operation, do not use an important file.
The actual permission check occurs when AWS attempts the S3 operation.
A read-only user should receive an Access Denied response for unauthorized write/delete operations.

### Important: The S3 console may display an Upload button even when the user does not have permission to complete the upload. The presence of the button alone does not prove that upload permission exists.

## Outputs
<img width="1920" height="1080" alt="Screenshot 2026-08-27 135910" src="https://github.com/user-attachments/assets/cec6fc2b-4953-461b-addd-184cd8c9a200" />
<img width="1920" height="1080" alt="Screenshot 2026-08-27 135919" src="https://github.com/user-attachments/assets/8cdd7fcb-c6bc-4b13-bfed-1e9b2b8b2ca0" />
<img width="1920" height="1080" alt="Screenshot 2026-08-27 135926" src="https://github.com/user-attachments/assets/6520c2ba-79b5-4e6c-b88e-5475ba1ad1ce" />
<img width="1920" height="1080" alt="Screenshot 2026-08-27 135938" src="https://github.com/user-attachments/assets/974df5f0-42e3-4965-bced-de41f8236e79" />
<img width="1905" height="870" alt="Screenshot 2026-08-27 140918" src="https://github.com/user-attachments/assets/ffb187ba-f473-4fbe-985a-3674ef907df9" />
<img width="1900" height="501" alt="Screenshot 2026-08-27 141155" src="https://github.com/user-attachments/assets/612e42d3-2f05-41ec-92a2-df8f81e8a63e" />

## Expected Result

The IAM group cloudSecurity_2026 is successfully created and assigned the AmazonS3ReadOnlyAccess policy. The IAM user student01 is successfully created, added to the group, and provided with AWS Management Console access. The user can log in to AWS and access the assigned S3 resources according to the permissions inherited from the group.
| **Entity Type** | **Name**             | **Permissions Attached**           | **MFA Enabled** | **Assigned Group**   |
| --------------- | -------------------- | ---------------------------------- | --------------- | -------------------- |
| Group           | `cloudSecurity_2026` | `AmazonS3ReadOnlyAccess`           | -               | -                    |
| User            | `student01`          | Inherits from `cloudSecurity_2026` | Yes             | `cloudSecurity_2026` |
| Role            | `S3-ReadOnly-Access` | `AmazonS3ReadOnlyAccess`           | N/A             | -                    |

## Result

Thus, Identity and Access Management (IAM) was successfully implemented in AWS by creating an IAM group, assigning an S3 read-only policy, creating an IAM user, enabling console access, and verifying permission-based access to Amazon S3.
