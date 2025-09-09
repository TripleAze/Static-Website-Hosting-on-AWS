# 🌐 Static Website Hosting on AWS (S3 + CloudFront + ACM)

## 📖 Project Overview
I built a static website hosted entirely on AWS using **Amazon S3, CloudFront, ACM, and IAM**.  
The site is globally distributed, secure with HTTPS, and fully within the **AWS Free Tier**.  

- **Use case:** Personal portfolio / static website.  
- **AWS Services:** S3, CloudFront, ACM, IAM (OAC).  
- **Cost:** $0 (Free Tier).  
- **Live Demo:** [Visit Site](https://d2cbpkvdkjqntq.cloudfront.net)  

---

## 🏗️ Architecture
![Architecture Diagram](Doc/Architecture-Diagram.png)

**Flow:**
1. User requests site → CloudFront distribution.  
2. CloudFront serves files from the S3 bucket.  
3. Bucket access is restricted via **Origin Access Control (OAC)**.  
4. ACM provides free SSL certificate for HTTPS.  

---

## ⚙️ Implementation Steps

1. **Provision S3 Bucket**
   - Created S3 bucket with static website hosting enabled.  
   - Uploaded `index.html` and assets.  

2. **Set up CloudFront Distribution**
   - Origin: S3 bucket.  
   - Viewer protocol policy: Redirect HTTP → HTTPS.  
   - Default root object: `index.html`.  

3. **Secure Bucket with OAC**
   - Removed public access.  
   - Attached **Origin Access Control** to CloudFront.  
   - Applied bucket policy to allow only CloudFront.  

4. **Enable HTTPS (ACM)**
   - CloudFront auto-assigned SSL certificate.  

5. **Invalidate Cache**
   - Created invalidation (`/*`) to refresh updated files.  

---

## 🚧 Challenges & Fixes
- **403 Forbidden (Access Denied)** → Solved by attaching OAC + updating bucket policy.  
- **404 NoSuchKey** → Fixed by uploading `index.html` to root + setting default root object.  

---

## ✅ Outcome
- Static site hosted with **global CDN distribution**.  
- Secure HTTPS access via CloudFront domain.  
- Free-tier friendly, no ongoing costs.  

---

## 📚 Key Learnings
- Hosting static websites on AWS S3.  
- Using CloudFront OAC for secure S3 access.  
- Enabling HTTPS with ACM.  
- Troubleshooting common S3/CloudFront errors.  

---

## 🔮 Next Steps
- Map a custom domain with **Route 53**.  
- Add **CI/CD pipeline** (CodePipeline + GitHub) for auto-deploys.  

---

## 📸 Screenshots
*(Add your site screenshots here)*  
