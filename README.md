# 🚀 AWS Image Analyzer

A lightweight, browser-based tool that allows users to upload images to Amazon S3 and analyze them using AWS Rekognition. Built with HTML, Tailwind CSS, and JavaScript, and deployed via GitHub Pages.

---

## 🌍 Live Demo

[Click here to try it out](https://jashanlol.github.io/aws-image-analyzer/)

---

## 📊 Features

* ✨ Drag and drop or click to select an image
* 🚀 Uploads image to Amazon S3 using presigned URLs
* 🔬 Analyzes the image using AWS Rekognition (labels with confidence)
* ⏳ Progress bar while uploading
* 📊 Displays confidence scores for recognized labels
* 💡 UX enhancements for loading, error handling, and reset between uploads

---

## 🌐 Technologies Used

* **Frontend:** HTML, Tailwind CSS, JavaScript
* **Backend:** AWS Lambda, API Gateway, Amazon Rekognition
* **Storage:** Amazon S3 (private bucket with presigned PUT)

---

## 🚧 Setup

### 1. Frontend

* All code is static (HTML/JS/CSS) and hosted via GitHub Pages

### 2. Backend (AWS)

* **Lambda function 1:** Generates S3 presigned URL for upload
* **Lambda function 2:** Accepts bucket and key, calls Rekognition DetectLabels
* **API Gateway:** Connected to both functions, with CORS properly configured
* **S3 Bucket:** Must have correct CORS, and policy allowing PUT via presigned URLs

---

## 💼 How It Works

1. User drags or selects an image
2. Frontend requests a presigned upload URL from API Gateway
3. Image is uploaded directly to S3
4. Frontend sends the image key to another API Gateway endpoint
5. Lambda calls AWS Rekognition, returns labels and confidence
6. Frontend displays the labels in a clean, readable format

---

## 🚫 Limitations

* Rekognition does **not** support formats like `.webp`, `.gif`, or `.heic`. Use `.jpg` or `.png`
* Images must be under 15MB (AWS Rekognition limit)

---

## 🔍 Example Labels Output

```
• Advertisement (99.51%)
• Poster (99.51%)
• Bird (86.89%)
• Person (57.27%)
```

---

## 📄 License

This project is open source. You may modify and use it under the [MIT License](LICENSE).

---

## 🙌 Acknowledgements

* Built using AWS SDKs, Rekognition API, and GitHub Pages
* Designed and deployed by Jashan Kaeley as a course project
