# Lab Solution: Host a Static Website on Amazon S3

**Student Name:** Balint Lojt  
**Date:** 09/07/2026  
**Lab Completion Time: 2 hours 10 min

---

## Part 1: Bucket Configuration

### Bucket Information

**Bucket Name: my-static-website-b-l-2026

**Region: us-east-1

**Bucket Website Endpoint URL:**
```
___________________________________________________________
```

**Screenshot 1: Bucket Creation Confirmation**
![Bucket Created](screenshots/01-bucket-created.png)

---

## Part 2: Static Website Hosting Configuration

### Configuration Details

**Index Document:** --index-document index.html

**Error Document:** --error-document error.html

**Screenshot 2: Static Website Hosting Settings**

<img width="938" height="86" alt="02-static-hosting-config" src="https://github.com/user-attachments/assets/03e4a1c0-56c4-4866-8f24-c40c07714479" />


## Part 3: Website Files

### Files Created

List the files you created:
1. index.html
2. styles.css
3. error.html

**Did you customize the HTML/CSS?
No

**If yes, describe your customizations:**
N/A

**Screenshot 3: Files Uploaded to S3**
<img width="1656" height="360" alt="03-files-uploaded" src="https://github.com/user-attachments/assets/a8a6aa0c-77e4-48ea-90e0-e91d2c301b1b" />





## Part 4: Bucket Policy

### Bucket Policy Applied

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-static-website-b-l-2026/*"
        }
    ]
}

**Screenshot 4: Bucket Policy Configuration**
<img width="987" height="331" alt="04-bucket-policy" src="https://github.com/user-attachments/assets/23b1d7ae-3899-4898-a369-74c58f51daa2" />


---

## Part 5: Testing and Verification

### Website Testing

**Website URL (from endpoint):**
http://my-static-website-b-l-2026.s3-website-us-east-1.amazonaws.com

**Did the website load successfully?** 
Yes

**Did the CSS styling apply correctly?** 
Yes

**Screenshot 5: Working Website**
<img width="1923" height="1142" alt="06-website-live" src="https://github.com/user-attachments/assets/3ee55ad2-1a8d-4df8-b61a-d6b68a8ec1f8" />


### Error Page Testing

**Test URL used:**
http://my-static-website-b-l-2026.s3-website-us-east-1.amazonaws.com/nonexistent.html

**Did custom error page display?**
yes

**Screenshot 6: Custom 404 Error Page**
<img width="1760" height="563" alt="06-error-page" src="https://github.com/user-attachments/assets/0fad89fe-1d94-47d3-8308-2ca524212004" />


---

## Part 6: CLI Commands Used

**Document all AWS CLI commands you executed:**

```bash
# Bucket creation
aws s3api create-bucket \
  --bucket my-static-website-b-l-2026 \
  --region us-east-1

# Enable website hosting
Did it from the console :(

# Upload files

aws s3 cp . s3://my-static-website-b-l-2026/ --recursive --region eu-north-1

# Apply bucket policy
aws s3api put-bucket-policy \
  --bucket my-static-website-b-l-2026 \
  --policy file://bucket-policy.json

# Verify configuration

aws s3 ls s3://my-static-website-b-l-2026/
aws s3api get-bucket-location --bucket my-static-website-b-l-2026
curl -i http://my-static-website-b-l-2026.s3-website-us-east-1.amazonaws.com/nonexistent.html




## Bonus Challenges Completed

- [ ] Challenge 1: Added about.html page
- [ ] Challenge 2: Used subdirectories for organization
- [ ] Challenge 3: Used `aws s3 sync` command

**Bonus Challenge Notes:**
N/A

---

## Reflection Questions

### 1. What are the advantages of S3 static hosting compared to traditional web servers?
S3 static hosting is a  money saver because it cuts out the need to run and manage 
EC2 instances or containers 24/7 just to serve frontend files (HTML/CSS/JS). No need to pay for idle compute time or OS maintenance. Just have to pay for the storage that is in use, and the data transfer.

### 2. Why is a bucket policy necessary for public website access?

By default, AWS locks down S3 buckets for security reasons.
Turning on the static website hosting feature gives an endpoint, 
but it doesn't automatically grant permission for people to actually read the files. 
A bucket policy is needed specifically to allow public read access.

### 3. What are the limitations of S3 static website hosting?

It can only handle static files (HTML, Css, JS, images), so no server-side code (Python, PHP).
It is also not secure, so it can only do normal HTTP and not HTTPS (less secure) 

### 4. When would you NOT use S3 for website hosting?

If it needs to run backend code. Strict compliance/security requirements.


### 5. How does S3 static hosting fit into cost optimization strategies?

Because it is static, I don't need to pay for EC2 instances or containers 24/7 to serve HTML and JS files.



## Troubleshooting Log

**Did you encounter any issues?
No

**If yes, document the issues and how you resolved them:**

| Issue | Error Message | Solution | Time to Resolve |
|-------|--------------|----------|-----------------|
|       |              |          |                 |
|       |              |          |                 |
|       |              |          |                 |

---

## Cleanup Confirmation

- [x] Emptied S3 bucket
- [x] Deleted S3 bucket
- [x] Verified no resources remain

**Cleanup CLI commands used:**
```bash
# Empty bucket


# Delete bucket


```

---

## Self-Assessment

**Rate your understanding of each concept (1-5, where 5 is expert):**

| Concept | Rating | Notes |
|---------|--------|-------|
| S3 bucket creation | ___/5 | |
| Static website hosting configuration | ___/5 | |
| Bucket policies and public access | ___/5 | |
| Uploading and managing S3 objects | ___/5 | |
| S3 website endpoints | ___/5 | |
| HTML/CSS basics | ___/5 | |

---

## Instructor Verification

**Instructor Name:** ___________________________

**Date Reviewed:** ___________________________

**Website URL Verified:** ☐ Yes ☐ No

**Comments:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

**Grade/Status:** ___________________________

---

## Additional Resources Referenced

List any documentation, tutorials, or resources you used:

1. ___________________________________________________________
2. ___________________________________________________________
3. ___________________________________________________________

---

**Lab Status:** ☐ Complete ☐ Needs Revision

**Total Time Spent:** ________ minutes

**Submission Date:** ___________________________
