# 🌐 Sample Static Website Deployment

This repository hosts a sample static HTML website that demonstrates a robust Continuous Integration/Continuous Deployment (CI/CD) pipeline using **GitHub Actions** and **AWS Cloud Services**.

## 🚀 Live Deployment

The latest version of this website is automatically deployed and served via AWS CloudFront:

**Live URL:** [https://d10i80a6xp157t.cloudfront.net/](https://d10i80a6xp157t.cloudfront.net/)

---

## ✨ Key Features

* **Static HTML/CSS:** Simple, fast, and scalable website structure.
* **AWS S3 Hosting:** Files are stored efficiently and durably in an S3 bucket configured for static website hosting.
* **AWS CloudFront CDN:** Content is served globally via CloudFront, ensuring low latency and fast load times.
* **Automated CI/CD:** Changes are deployed instantly upon merging to the `main` branch using GitHub Actions.

---

## ⚙️ CI/CD Pipeline Overview

This project uses a GitHub Actions workflow (`.github/workflows/deploy.yml`) to manage the entire deployment process.

### **Workflow:**

1.  **Trigger:** Any commit or merge to the **`main`** branch initiates the workflow.
2.  **Authentication:** GitHub Actions uses secure **GitHub Secrets** (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`) to assume an IAM role for AWS access.
3.  **Deployment:** The `aws s3 sync` command copies all local files to the designated S3 bucket (`s3://<YOUR_BUCKET_NAME>`). The `--delete` flag ensures old or removed files are also deleted from the bucket.
4.  **Cache Invalidation:** The workflow executes an `aws cloudfront create-invalidation` command, forcing the CloudFront distribution (`d10i80a6xp157t`) to clear its cache and immediately fetch the new files from S3, ensuring changes reflect instantly for all users.

### **Setup Requirements (For Maintenance/Modification):**

To run this workflow, the following environment variables (stored as GitHub Secrets) must be configured in the repository settings:

| Secret Name | Purpose |
| :--- | :--- |
| `AWS_ACCESS_KEY_ID` | IAM User Access Key |
| `AWS_SECRET_ACCESS_KEY` | IAM User Secret Key |
| `S3_BUCKET_NAME` | The exact S3 bucket name |
| `CLOUDFRONT_DISTRIBUTION_ID` | The ID of the CloudFront distribution (`D10I80A6XP157T`) |

---

## 💻 Local Development

To run and test the website locally:

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/syerrawa/sample-website.git](https://github.com/syerrawa/sample-website.git)
    cd sample-website
    ```
2.  **Open:** Simply open the `index.html` file in your web browser.

---

## 🤝 Contribution

Feel free to suggest improvements to the sample code or the deployment pipeline!