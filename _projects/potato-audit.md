---
layout: project
title: Potato Audit
date: 2024-03-20
tags: [Python, React, Flask, OCR, Computer Vision, Web Automation]
problem: "Auditors manually processing thousands of documents and announcements, leading to inefficiencies and potential errors"
approach: "Built an end-to-end automation solution with multiple iterations, ultimately landing on an interactive web interface for document processing"
demo_url: "https://github.com/eaziym/potato-audit-public"
metrics:
  - label: Processing Time Reduction
    value: "95%"
  - label: Accuracy Rate
    value: "~100%"
  - label: Documents/Day
    value: "1000+"
cover_image: /assets/images/potato-audit.png
images:
  - path: /assets/images/potato-audit-interface.png
    caption: Main interface
---

## The Journey

### 1. Problem Identification

During my audit internship, I observed critical inefficiencies:

- Auditors manually matching printed documents with accounting system entries
- Hours spent downloading and compiling public announcements from exchanges
- High risk of human error in data extraction
- Need for structured compilation of data for audit documentation

### 2. Solution Evolution

#### Initial Approach: LLM-Based Extraction

Initially attempted using Large Language Models for document parsing:

```python
def extract_fields_llm(text):
    prompt = """
    As an AI specialized in analyzing invoice documents, extract:
    - invoice number
    - invoice date
    - buyer name
    - seller name
    - amount before GST
    - amount after GST

    Format: JSON
    Text: {text}
    """
    response = llm_client.complete(prompt)
    return parse_json(response)
```

**Challenges Faced:**

- Slow processing (2-3 seconds per document)
- Inconsistent accuracy (~75%)
- High API costs for production scale
- Difficulty handling varied document formats

#### Final Approach: Interactive Spatial Recognition

Developed a user-friendly solution using bounding box selection:

```python
@app.route('/process-selected-pairs', methods=['POST'])
def process_selected_pairs():
    # Process documents based on user-selected coordinates
    invoice_files = [f for f in os.listdir(directoryPath) if f.lower().endswith(('.pdf', '.png'))]
    progress['total'] = len(invoice_files)

    for index, invoice_file in enumerate(invoice_files):
        # Extract text and coordinates from document
        processed_path, invoice_blobs, invoice_merged_texts = process_invoice_image(invoice_path)

        # Use saved spatial relationships to find corresponding values
        for label_text, (dx, dy) in spatial_relationships.items():
            label_box = find_coordinates_by_text(label_text, invoice_merged_texts)
            if label_box:
                value_coords = apply_spatial_relationship(label_box, dx, dy)
                closest_box = find_closest_box(dx, dy, value_coords, invoice_merged_texts)
```

This approach:

- Allows users to visually select label-value pairs in documents
- Saves spatial relationships for future automated processing
- Achieves near 100% accuracy with human verification
- Processes subsequent documents automatically using learned patterns

#### Exchange Data Automation

Built a scalable scraping system:

- Handles multiple exchanges (SGX, ASX)
- Automated announcement downloads and PDF extraction
- Smart retry mechanisms and rate limiting
- Structured Excel report generation
- Email notification system for daily updates

### 3. Technical Implementation

#### Document Processing Pipeline

1. **Document Preprocessing**

   - PDF/Image conversion using Poppler
   - OCR with Tesseract
   - Text block detection with coordinates

2. **Interactive Field Selection**

   - Web interface for bounding box selection
   - Visual confirmation of selected fields
   - Spatial relationship learning
   - Batch processing with learned patterns

3. **Validation & Output**
   - Preview of extracted fields
   - Manual correction if needed
   - Excel/JSON export options
   - Processing audit trail

#### Modern Web Interface

- React frontend with Material-UI
- Interactive document viewer
- Real-time processing status
- Batch upload capabilities
- Visual field selection tools
- Export functionality

### 4. Key Learnings

1. **User-Centric Design**

   - Initially over-engineered with LLMs
   - Simplified to intuitive visual interface
   - Balance automation with user control
   - Importance of immediate visual feedback

2. **Automation Strategy**

   - Learn from user interactions
   - Store spatial relationships for reuse
   - Handle document variations gracefully
   - Maintain high accuracy with minimal user input

3. **Technical Evolution**
   - Started with complex ML approach
   - Pivoted to simpler, more reliable solution
   - Focused on user experience
   - Built for maintainability and scalability

### 5. Impact

- Reduced document processing time from hours to minutes
- Achieved near 100% accuracy with human verification
- Eliminated manual announcement compilation
- Standardized output format for audit documentation
- Scalable to handle thousands of documents daily

### 6. Technologies Used

- Frontend: React, Material-UI
- Backend: Flask, Python
- Document Processing: Tesseract OCR, Poppler
- Web Automation: Selenium
- Data Processing: Pandas
- Email Integration: SMTP
- PDF Processing: PyMuPDF

[View on GitHub](https://github.com/eaziym/potato-audit-public)
[View PDF Introduction](/assets/docs/Potato_Audit_Manual.pdf)
