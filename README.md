# AWS Image Analyzer

**AWS Image Analyzer** is a browser-based web application that allows users to upload images to Amazon S3 and analyze them using AWS Rekognition. It demonstrates full-stack integration between a static frontend and serverless AWS services. The tool was developed as part of a course project on cloud-based application development.

---

## Live Demo

[https://jashanlol.github.io/aws-image-analyzer/](https://jashanlol.github.io/aws-image-analyzer/)

---

## Project Overview

This project showcases a complete image processing pipeline using Amazon Web Services. Users can upload an image, which is then analyzed using AWS Rekognition to detect labels and their confidence scores. The application provides a clean and responsive user interface with real-time feedback and progress indication.

---

## Key Features

- Upload image via drag-and-drop or file picker
- Upload directly to Amazon S3 using presigned URLs
- Analyze images using AWS Rekognition (`DetectLabels`)
- Display labels with associated confidence scores
- Visual upload progress bar and dynamic result rendering
- Handles common errors and enforces file format/size constraints

---

## Technologies Used

### Frontend

- HTML5
- Tailwind CSS (compiled via Tailwind CLI)
- Vanilla JavaScript

### Backend (AWS)

- AWS Lambda (Node.js runtime)
- Amazon API Gateway
- Amazon Rekognition
- Amazon S3 (with CORS and presigned URL configuration)

---

## System Architecture

1. User selects an image via drag-and-drop or input.
2. Frontend sends a request to API Gateway to obtain a presigned upload URL.
3. Image is uploaded directly to a private S3 bucket using the presigned URL.
4. A second API request (via API Gateway) sends the uploaded file’s key to a separate Lambda function.
5. Lambda uses the AWS Rekognition API to analyze the image and return labels and confidence values.
6. Frontend renders the results for the user.

---

## Setup Instructions

### Frontend

- Static files (`index.html`, `input.css`, `output.css`, `script.js`) are compiled and deployed to GitHub Pages.
- Tailwind CSS is compiled locally using the Tailwind CLI (`npm run build:css`).

### Backend (AWS)

- **Lambda Function 1:** Generates presigned PUT URLs for uploading to S3.
- **Lambda Function 2:** Receives the image key and returns Rekognition analysis.
- **API Gateway:** Exposes both Lambda functions via public HTTPS endpoints.
- **S3 Bucket:** Must support CORS for uploads and allow PUT via presigned URLs. Files remain private.

---

## Limitations

- Supported formats: `.jpg`, `.jpeg`, `.png`
- Unsupported formats: `.webp`, `.gif`, `.heic`
- Image size must not exceed 15 MB (Rekognition limitation)
- Requires internet access and valid AWS credentials for backend services

---

## Example Output

```
• Advertisement (99.51%)
• Poster (99.51%)
• Bird (86.89%)
• Person (57.27%)
```

---

## License

This project is released under the [MIT License](LICENSE).

---

## Author

Developed by **Jashan Kaeley**  
Submitted for course credit as part of [Course Name / Institution, if needed]