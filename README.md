# n8n-email-spam-filter
An automated email spam detection and filtering workflow built with n8n. Integrates Gmail triggers with CleanTalk and Hugging Face APIs to classify, filter, and manage incoming emails using multi-layer AI and external spam checks for enhanced email security and organization.

# n8n Email Spam Detection & Filtering Workflow

## Description
An automated email spam detection and filtering workflow built with n8n. Integrates Gmail triggers with CleanTalk and Hugging Face APIs to classify, filter, and manage incoming emails using multi-layer AI and external spam checks for enhanced email security and organization.

## Features
- Automated email retrieval via Gmail integration
- Dual spam detection using CleanTalk API and Hugging Face ML models
- Conditional workflow branching based on combined API results
- Multi-stage AI filtering for refined email classification
- Modular and extensible design using n8n's visual workflow editor


## How It Works
1. **Trigger & Retrieval**  
   Starts on new email arrival using Gmail Trigger, fetching email content and metadata.

2. **Preprocessing**  
   Custom code node parses and organizes message data for API requests.

3. **Spam Detection**  
   Parallel calls to CleanTalk and Hugging Face APIs analyze emails for spam likelihood. Outcomes are merged.

4. **Conditional Routing**  
   Based on merged results, the workflow either halts or proceeds to further AI filtering.

5. **Advanced Filtering**  
   Additional Hugging Face API calls perform refined classification for detailed email management.

6. **Extensibility**  
   Easily extend this workflow to perform actions like archiving, labeling, or forwarding based on classification.

## Setup

### Prerequisites
- n8n instance (cloud or self-hosted)
- Gmail API credentials configured in n8n
- CleanTalk API key (https://cleantalk.org)
- Hugging Face API key (https://huggingface.co/)
- Basic familiarity with n8n workflow editor


<img width="1077" height="274" alt="Screenshot 2025-10-31 at 10 34 49 PM" src="https://github.com/user-attachments/assets/355827e7-293d-411d-b282-03e135a207e0" />


