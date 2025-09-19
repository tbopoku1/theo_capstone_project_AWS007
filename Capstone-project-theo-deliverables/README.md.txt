# Serverless Text-to-Speech (TTS) Web App

## Project Overview
This is a **serverless web application** that converts text into speech using **AWS Lambda**, **Amazon Polly**, **S3**, and **API Gateway**. Users can type text, select a voice, and generate an MP3 audio file that plays directly in the browser.

**Use Cases:**
- Converting blog posts or articles to audio
- Reading books or short passages
- Quick text-to-speech conversion

---

## Architecture
![Architecture Diagram](architecture-diagram.png)

**Components:**
1. **Frontend** – HTML, CSS, and JS served locally, providing a text input, voice selection, and audio player.  
2. **API Gateway** – Exposes the Lambda function as a REST API endpoint (`POST /tts`).  
3. **Lambda Function** – Receives text and voice selection, calls Amazon Polly, and saves audio files to S3.  
4. **S3 Bucket** – Stores generated audio files securely.  
5. **Amazon Polly** – Converts text into speech.

---

## Folder Structure
serverless-tts-app/
│
├── frontend/                     # Static web frontend
│   ├── index.html                 # Main HTML page
│   ├── scripts.js                 # JavaScript logic (API calls, audio playback)
│   └── style.css                  # Styling for the web app
│
├── lambda/                        # AWS Lambda function
│   ├── lambda_function.py         # Python code for text-to-speech
│   └── lambda.zip                 # Packaged Lambda deployment file
│
├── terraform/                     # Infrastructure as Code (Terraform)
│   ├── modules/                   # Reusable Terraform modules
│   │   ├── api/                   # API Gateway module
│   │   │   ├── main.tf
│   │   │   ├── outputs.tf
│   │   │   └── variables.tf
│   │   ├── lambda/                # Lambda module
│   │   │   ├── main.tf
│   │   │   ├── outputs.tf
│   │   │   └── variables.tf
│   │   └── s3/                    # S3 module
│   │       ├── main.tf
│   │       ├── outputs.tf
│   │       └── variables.tf
│   │
│   ├── main.tf                    # Root Terraform configuration
│   ├── outputs.tf                 # Global output values
│   └── variables.tf               # Global variables
│
├── architecture-diagram.png       # Visual architecture diagram
└── README.md                      # Project documentation



---

## Features
- Converts text to speech in real-time  
- Selectable English voices (Joanna, Matthew, Ivy, Justin)  
- Audio stored in S3 for playback  
- Fully serverless architecture  
- Beginner-friendly Terraform Infrastructure-as-Code setup  

---

## Prerequisites
- **AWS Account** with free tier eligibility  
- **AWS CLI** installed and configured  
- **Terraform** installed  
- Browser to access the frontend  

---

## Setup Instructions

### 1. Deploy Terraform Infrastructure
```bash
cd terraform
terraform init
terraform apply

### 2. Package Lambda Function
```bash
cd ../lambda
zip tts_lambda.zip tts_lambda.py

### 3. Get API Endpoint
```bash
terraform output api_endpoint

### 4. Open Frontend
Open frontend/index.html in your browser.
Enter text, select a voice, and click Convert to Speech.
The audio will play directly from S3.

**Web App URL**
http://theo123-text-to-speech.s3-website-us-east-1.amazonaws.com

**Notes**
Only English voices are supported (Amazon Polly does not translate text).
The app is designed to stay within AWS Free Tier, but exceeding free limits may incur charges.
Ensure your AWS credentials have permissions for Lambda, S3, Polly, and API Gateway.

**Author**
Developed by [Theophilus Boakye Opoku]
Contact: [theophilusopokuboakye@gmail.com]

##Deliverables Included
*Terraform folder*
..Root files: main.tf, variables.tf, outputs.tf
..Modules:
...api → main.tf, variables.tf, outputs.tf
...lambda → main.tf, variables.tf, outputs.tf
...s3 → main.tf, variables.tf, outputs.tf
*Lambda folder*
..lambda_function.py
..lambda.zip
*Frontend folder*
..index.html
..style.css
..scripts.js
*Architecture diagram*
..architecture-diagram.png
*README.md*
..Project documentation