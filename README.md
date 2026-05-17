# Vartis Care AI

<h3 align="center">
AI-Powered Healthcare Resource Navigation Platform
</h3>

<p align="center">
Built for healthcare social workers, patient advocates, and intelligent care coordination.
</p>

<p align="center">
<img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Streamlit-Frontend-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" />
<img src="https://img.shields.io/badge/Claude%203.5-Anthropic-8A2BE2?style=for-the-badge" />
<img src="https://img.shields.io/badge/RAG-Pipeline-84CC16?style=for-the-badge" />
<img src="https://img.shields.io/badge/LSU-CSC%207644-461D7C?style=for-the-badge" />
</p>

---

## Platform Preview

<img width="1631" height="1065" alt="image" src="https://github.com/user-attachments/assets/4e26fc97-0186-4b83-998d-483fd3b47d49" />

```

---

## Overview

Vartis Care AI is an AI-powered decision-support system that extracts patient eligibility information from unstructured intake notes and clinical documents, then matches patients to verified community resources.

The platform is designed to help healthcare social workers and patient navigators reduce manual search time, improve referral accuracy, and limit referral dead-ends for vulnerable patients.

This project was developed as the final project for **CSC 7644: Applied LLM Development** at **Louisiana State University**.

---

## Why This Matters

Healthcare advocates often spend hours manually searching for assistance programs while patients wait for urgent support.

Vartis Care AI brings together AI-powered extraction, structured eligibility matching, retrieval-augmented generation, and human-in-the-loop advocate review to support faster and more reliable care navigation.

---

## Core Capabilities

| Feature | Description |
|---|---|
| AI Extraction | Extracts eligibility markers from intake notes and clinical documents |
| Resource Matching | Matches patients to verified assistance programs |
| Patient Profile | Displays structured patient information for advocate review |
| Search & Filters | Filters resources by need type, source, confidence, and keyword |
| Human Review | Requires advocate approval before referral delivery |
| RAG Pipeline | Supports retrieval-based recommendations and planned agentic fallback |
| Structured Output | Returns clean JSON eligibility profiles and matched resources |

---

## Key Features

- Extracts structured eligibility markers including income level, zip code, diagnosis, insurance status, household size, and urgency
- Matches patients to verified Atlanta-area community resources
- Organizes resources across need categories such as medication, medical care, food, utilities, rent, housing, employment, and clothing
- Displays professional resource cards with confidence scores, addresses, phone numbers, and websites
- Includes a human-in-the-loop advocate review workflow
- Supports simulated patient chart upload and advocate notes documentation
- Designed for future RAG expansion using ChromaDB and external resource APIs

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3.10+ |
| Frontend | Streamlit |
| AI Model | Claude 3.5 Sonnet via Anthropic API |
| Retrieval | ChromaDB |
| Evaluation | DeepEval |
| Architecture | RAG Pipeline, Structured JSON Extraction, Agentic Fallback |
| Workflow | Human-in-the-Loop Advocate Review |

---

## System Architecture

```text
Patient Intake Note / Clinical Document
              |
              v
Claude 3.5 Sonnet
AI Eligibility Extraction
              |
              v
Structured JSON Patient Profile
              |
              v
RAG Router
       /                 \
      v                   v
ChromaDB            External APIs
Resource Corpus     FindHelp / 211 / NPPES
      \                   /
              v
Ranked Resource Recommendations
              |
              v
Advocate Review Interface
              |
              v
Approved Referral Delivered to Patient
```

---

## Repository Structure

```text
vartis-care-ai/
|
|- app.py              # Streamlit web interface
|- extractor.py        # Eligibility extraction and resource matching logic
|- vartis_agent.py     # Command-line pipeline coordinator
|- intake_sample.txt   # Sample de-identified intake note
|- requirements.txt    # Python dependencies
|- .env.example        # Environment variable template
|- .gitignore          # Files excluded from version control
|- README.md           # Project documentation
```

---

## Setup Instructions

### Prerequisites

- Python 3.10 or higher
- pip
- Anthropic API key
- Windows, macOS, or Linux

---

### Step 1: Clone the Repository

```bash
git clone https://github.com/Chantel-W-CodesLSU/csc7644-final-project-walker-VARTIS-AI.git
cd csc7644-final-project-walker-VARTIS-AI
```

---

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

---

### Step 3: Configure Environment Variables

Copy the example environment file:

```bash
cp .env.example .env
```

Open `.env` and add your Anthropic API key:

```env
ANTHROPIC_API_KEY=your_key_here
```

Do not commit your `.env` file.

---

## Running the Application

### Streamlit Web App

```bash
streamlit run app.py
```

The app will open at:

```text
http://localhost:8501
```

---

## How to Use the App

1. Fill in the patient profile fields
2. Enter or upload intake information
3. Allow the system to extract eligibility markers
4. Review matched community resources
5. Filter recommendations by need type, source, confidence, or keyword
6. Add advocate notes
7. Complete the human-review checklist
8. Upload the approved referral summary to the patient chart

---

## Example Output

```json
{
  "income_level": "below_200_fpl",
  "zip_code": "30301",
  "diagnosis_code": "I10",
  "insurance_status": "uninsured",
  "matched_resources": [
    {
      "need_type": "MEDICATION",
      "name": "GoodRx - Prescription Discount Program",
      "address": "Available online and at local pharmacies",
      "website": "https://www.goodrx.com",
      "source": "findhelp_api",
      "confidence": 0.97
    }
  ]
}
```

---

## Resource Categories

The system organizes recommendations across the following categories:

- Medication Assistance
- Medical Care
- Food Assistance
- Utility Assistance
- Rent Assistance
- Housing Support
- Employment Resources
- Clothing Assistance

Each resource includes available details such as address, phone number, website, source, and confidence score.

---

## Future Improvements

- Secure cloud deployment
- HIPAA-aligned infrastructure design
- Live FindHelp and 211 API integrations
- Multi-patient dashboard
- Vectorized PDF corpus ingestion
- Real-time recommendation ranking
- Improved resource verification workflow
- Role-based access control for advocates
- Audit logging for sensitive workflow actions
- Expanded RAG evaluation with faithfulness and contextual recall metrics

---

## Project Impact

Vartis Care AI demonstrates how large language models can support healthcare navigation by reducing manual search burden, improving structured intake review, and helping advocates identify relevant resources more efficiently.

The system is not a replacement for professional judgment. It is designed as a decision-support tool that keeps human advocates in control of final review and referral approval.

---

## Author

**Chantel Walker**  
Graduate Computer Science Student  
Louisiana State University  
CSC 7644: Applied LLM Development  
Spring 2026


---

## References

- Anthropic Claude API Documentation
- Streamlit Documentation
- ChromaDB Documentation
- DeepEval Documentation
- FindHelp.org API
- 211 National Data Platform
- Lewis et al. (2020), Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks
