# JanSathi AI+ – System Design Document

## 1. Overview

JanSathi AI+ is a voice-first AI assistant that enables citizens to access government schemes and file grievances using natural voice interaction.

This document describes:

- The Hackathon Demo Architecture (implemented)
- The Production Architecture Vision (future roadmap)

The demo focuses on a Hindi voice-based assistant that demonstrates eligibility matching and grievance filing using AWS serverless infrastructure.

---

# 2. Hackathon Demo Architecture (Implemented)

## 2.1 Design Goals

The hackathon implementation prioritizes:

- End-to-end working voice flow
- AWS-native serverless integration
- Minimal infrastructure complexity
- Clear scalability pathway
- Stable live demo performance

---

## 2.2 High-Level Demo Flow

1. User speaks Hindi query
2. Audio sent to backend
3. Amazon Transcribe converts speech → text
4. Text processed via AWS Lambda
5. Intent + eligibility handled via Amazon Bedrock
6. Scheme results or grievance response generated
7. Amazon Polly converts response → Hindi speech
8. Response returned to user
9. Grievance stored in DynamoDB (if filed)

---

## 2.3 Demo Architecture Components

### Frontend
- Static Web Application
- Hosted on Amazon S3
- Distributed via CloudFront
- Audio recording via browser APIs

---

### API Layer
- Amazon API Gateway
- REST endpoints:
  - /transcribe
  - /process
  - /grievance

---

### Compute Layer
- AWS Lambda (4 Functions)

1. Speech Processing Lambda
2. Intent & Eligibility Lambda
3. Grievance Handler Lambda
4. Response Formatter Lambda

---

### AI Layer
- Amazon Bedrock
  - Claude 3 Haiku (intent + response)
  - Titan Embeddings (scheme similarity matching)

---

### Voice Services
- Amazon Transcribe (Hindi STT)
- Amazon Polly (Hindi TTS – Aditi voice)

---

### Data Layer
- Amazon DynamoDB
  - Scheme dataset (5 schemes)
  - Grievance records
  - Session metadata

---

## 2.4 Demo Scope Constraints

### Supported Language
- Hindi only (voice input + output)

### Implemented Features
- Voice-based interaction
- 5-scheme eligibility matching
- Grievance tracking ID generation
- Basic session management
- Serverless AWS deployment

---

## 2.5 Not Included in Hackathon Demo

The following are part of production roadmap but not implemented in demo:

- Regional languages beyond Hindi
- Automatic language detection
- Authentication (Cognito)
- Document upload & OCR
- Real-time grievance routing
- Human fallback queue
- Multi-region deployment
- Advanced monitoring & alerting
- Auto-scaling validation
- CI/CD pipelines

---

# 3. Eligibility Matching Design

## 3.1 Approach

The eligibility system uses a hybrid approach:

1. Structured rule-based filtering:
   - Age
   - Occupation
   - Income
   - Gender
   - State

2. Vector similarity matching:
   - Titan embeddings for scheme description comparison

3. Confidence scoring:
   - Top 3 schemes displayed with score %

---

## 3.2 Supported Schemes (Demo Dataset)

- PM-KISAN
- Ayushman Bharat
- PM Awas Yojana
- National Social Assistance Programme
- Sukanya Samriddhi Yojana

Dataset is pre-loaded in DynamoDB.

---

# 4. Grievance Filing System

## 4.1 Flow

1. User describes issue
2. Bedrock extracts structured fields:
   - Category
   - Description
3. Unique tracking ID generated:
   - Format: GRV-YYYYMMDD-XXXXX
4. Stored in DynamoDB
5. Confirmation message returned

No routing or escalation logic included in demo.

---

# 5. Low-Bandwidth Design Considerations

The demo simulates Bharat-ready optimization:

- MP3 audio compression (32 kbps)
- <50 KB API payload
- Server-side processing
- No client-side ML

Actual adaptive network detection not implemented.

---

# 6. Security Considerations (Demo Level)

- HTTPS via API Gateway
- IAM roles for service isolation
- No authentication layer in demo
- No PII persistence beyond grievance data

Production security features are deferred.

---

# 7. Production Architecture Vision

The system is designed to scale toward:

- Support for 22 scheduled Indian languages
- Automatic language detection
- Hybrid RAG with OpenSearch
- Cognito-based authentication
- Consent management
- Real-time grievance routing
- Officer dashboard
- Human fallback escalation
- Multi-region failover
- WAF + GuardDuty integration
- CI/CD automation
- Infrastructure as Code (Terraform)

The hackathon demo validates the core workflow that will support this full architecture.

---

# 8. Scalability Strategy

Current:
- Single-region deployment
- Lambda-based auto-scaling

Future:
- Multi-AZ deployment
- Caching layer (ElastiCache)
- Read replicas
- Global distribution

---

## 9. Cost Model (Demo)

Estimated demo cost (48-hour hackathon usage):
Approximately ₹3,000 – ₹4,000

Primary Cost Drivers:
- Amazon Bedrock API calls
- Amazon Transcribe audio processing
- Amazon Polly speech synthesis
- AWS Lambda execution time

The serverless architecture ensures pay-per-use billing and cost-efficient scaling. Lambda execution time

---

# 10. Conclusion

The hackathon prototype successfully demonstrates:

- Voice-first AI public service access
- Eligibility-based scheme discovery
- Simplified grievance filing
- Serverless AWS architecture

The design intentionally limits demo complexity while establishing a scalable production foundation.

JanSathi AI+ represents a practical, AI-powered approach to bridging India’s digital governance gap.

