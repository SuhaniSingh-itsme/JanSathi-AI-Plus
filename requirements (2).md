# JanSathi AI+  
### Talk to the Government. Not to a Website.

## Overview

JanSathi AI+ is a voice-first AI assistant designed to simplify access to Indian government schemes and grievance services. It enables citizens—especially those with limited digital literacy—to interact with public services using natural voice conversations instead of complex websites and forms.

The hackathon prototype demonstrates a Hindi voice-enabled AI assistant that helps users:

- Discover eligible government schemes  
- Understand benefits and requirements  
- File grievances and receive tracking IDs  

The platform is built on AWS serverless architecture and designed for future multilingual expansion across Bharat.

---

## Problem Statement

Millions of citizens in India struggle to access government services due to:

- Language barriers  
- Low digital literacy  
- Complex online portals  
- Limited internet connectivity  

As a result, many eligible beneficiaries miss critical schemes or depend on intermediaries, increasing misinformation and inefficiency.

---

## Hackathon MVP Scope

The hackathon implementation focuses on demonstrating a working end-to-end voice workflow within 48 hours.

### Demo Capabilities

- Hindi voice input using Amazon Transcribe  
- AI-powered response generation using Amazon Bedrock  
- Text-to-speech output using Amazon Polly  
- Scheme eligibility matching for 5 central government schemes  
- Grievance filing with tracking number generation  
- DynamoDB-based status storage  
- Serverless AWS architecture  

### Supported Language (Demo)

- Hindi (Voice + AI responses)

### Not Included in Demo (Production Features)

- Regional languages beyond Hindi  
- Automatic language detection  
- OCR document processing  
- Authentication (Cognito)  
- Real-time grievance routing  
- Human escalation system  
- Multi-region deployment  
- Advanced monitoring and security controls  

---

## Core Features

### 1. Voice-First Interaction
Users can speak queries in Hindi. The system converts speech to text, processes it using AI, and responds via synthesized speech.

### 2. AI-Powered Scheme Eligibility
The assistant asks simple questions (age, occupation, income, state) and recommends top matching schemes with confidence scores.

Demo includes:
- PM-KISAN  
- Ayushman Bharat  
- PM Awas Yojana  
- National Social Assistance Programme  
- Sukanya Samriddhi Yojana  

### 3. Grievance Filing
Users can describe complaints via voice or text.  
The system:
- Categorizes complaint  
- Generates structured record  
- Creates tracking ID  
- Stores status in DynamoDB  

### 4. Low-Bandwidth Awareness
The demo simulates:
- Audio compression  
- Small payload responses  
- Server-side processing for low-end devices  

---

## Architecture (Hackathon Demo)

### Frontend
- Static web app hosted on S3
- Delivered via CloudFront

### Backend
- Amazon API Gateway
- AWS Lambda (business logic)
- Amazon Bedrock (Claude 3 Haiku + Titan Embeddings)
- Amazon Transcribe (Hindi STT)
- Amazon Polly (Hindi TTS)
- Amazon DynamoDB (data storage)

All services run in a single AWS region for demo simplicity.

---

## Production Vision (Post-Hackathon)

The architecture is designed to scale toward:

- Support for 22 scheduled Indian languages  
- Adaptive multilingual voice detection  
- Advanced RAG pipeline with hybrid search  
- Secure authentication & consent management  
- Real-time grievance routing and escalation  
- Multi-region high-availability deployment  
- Document upload + OCR  
- Human fallback queue  

---

## Technical Stack

- AWS Lambda  
- Amazon API Gateway  
- Amazon Bedrock  
- Amazon Transcribe  
- Amazon Polly  
- Amazon DynamoDB  
- Amazon S3  
- Amazon CloudFront  

---

## Estimated Demo Cost

- Estimated hackathon demo cost: < $50  
- Serverless, pay-per-use architecture  
- Designed for cost-efficient scaling  

---

## Social Impact

JanSathi AI+ aims to:

- Empower low-literacy citizens through voice-first access  
- Reduce dependency on intermediaries  
- Improve transparency in grievance processes  
- Enable inclusive digital governance  

The platform demonstrates how AI can bridge the digital divide and make government services accessible to every citizen in Bharat.

---

## Team

Team Name: AI4People  
Project: JanSathi AI+  

---

## Demo Flow (For Judges)

1. User speaks Hindi query  
2. Audio converted to text  
3. AI processes request  
4. Scheme suggestions displayed  
5. User files grievance  
6. Tracking ID generated  

---

JanSathi AI+  
Voice Access. Inclusive Governance. Digital Bharat.