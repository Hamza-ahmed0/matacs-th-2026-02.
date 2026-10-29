MATACS Associate Software Developer Assessment

Candidate Information

Full Name: Hamza Ahmed

Assessment Reference: MATACS-TH-2026-02

Time Spent: 3 Hours

USAGE OF AI:

I USed AI to create every diagram , file and structure of code also, Because I used Ai as my assistant not the actually design only with help of Ai, I spend y tim eot understand the architecture of projct and requirments of rpojects, then design 2  approach and ask some approaches woth Ai also and finalize my pointof view give proper script to AI to create every file according to my design.

Project Overview

This project evaluates commercial solar installation proposals using AI-assisted information extraction and deterministic scoring logic. It extracts proposal details from PDF files, checks mandatory eligibility requirements, calculates weighted scores for eligible proposals, and generates a structured JSON ranking.

The system is designed to support procurement decisions while flagging proposals that require human review.

Repository Files

File

Description

Evaluate.js

Main Node.js evaluation script

extracted_proposals.json

Extracted proposal details and evidence

ranking.json

Final simplified proposal ranking

WRITEUP.md

Assessment write-up and design decisions

PROMPTS.md

AI prompts used during development

Architecture Diagram

System architecture diagram

package.json

Project dependencies and package configuration

.gitignore

Files excluded from version control

Technology Stack

Node.js

Groq API

Large Language Model (LLM) for proposal information extraction

pdf-parse for PDF text extraction

dotenv for environment configuration

JSON for structured outputs

How to Run

Prerequisites

Node.js and npm

A valid Groq API key

Proposal PDFs placed in the input/ directory

Setup

Install dependencies:

npm install

Create a .env file in the project root:

GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=openai/gpt-oss-120b

Add the proposal PDFs to the input/ directory.

Run the evaluation:

node Evaluate.js

The script generates extracted_proposals.json and ranking.json.