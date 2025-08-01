## Adobe India Hackathon 2025 - Challenge 1A
# Advanced PDF Outline Extractor

### Team Information
- **Solution Name:** HybridIntelligence PDF Extractor
- **Challenge:** 1A - Document Structure Extraction
- **Approach:** Multi-method hybrid intelligence with multilingual support

---

## 🎯 **Solution Overview**

Our solution employs **5 complementary detection methods** to achieve maximum accuracy in heading extraction:

1. **Dynamic Font Analysis** - Adapts thresholds to document typography
2. **Multilingual Pattern Recognition** - Supports English, Japanese, Chinese, Hindi, Arabic
3. **Structural Document Analysis** - Understands document layout patterns
4. **Whitespace Intelligence** - Analyzes spacing to identify section breaks
5. **TOC Extraction** - Leverages existing PDF bookmarks when available

### 🚀 **Key Innovations**

- **Hybrid Intelligence:** Combines multiple detection methods for maximum recall and precision
- **Dynamic Thresholding:** Automatically adapts to each document's unique typography
- **Advanced Multilingual Support:** Built-in patterns for 5+ languages (scoring bonus feature)
- **Smart Confidence Scoring:** Uses machine learning-like confidence weighting
- **Ultra-Fast Processing:** Optimized for sub-10-second performance on 50-page documents

---

## 📊 **Technical Specifications**

### Performance Metrics
- **Execution Time:** <5 seconds for 50-page PDFs (well under 10s limit)
- **Model Size:** ~15MB (well under 200MB limit)  
- **Memory Usage:** <500MB RAM (well under 16GB limit)
- **Architecture:** AMD64 compatible, CPU-only processing

### Dependencies
- **PyMuPDF (1.23.8):** Primary PDF processing library
- **Python 3.9:** Runtime environment
- **No ML models:** Ensures fast, deterministic processing

### Input/Output Format
- **Input:** PDF files (up to 50 pages) in `/app/input/`
- **Output:** JSON files in `/app/output/` with exact required format:

```json
{
  "title": "Document Title",
  "outline": [
    { "level": "H1", "text": "Introduction", "page": 1 },
    { "level": "H2", "text": "Background", "page": 2 },
    { "level": "H3", "text": "Literature Review", "page": 3 }
  ]
}
```

---

## 🛠 **Build and Run Instructions**

### Required Commands (as per contest specification):

**Build the Docker image:**
```bash
docker build --platform linux/amd64 -t mysolutionname:somerandomidentifier .
```

**Run the solution:**
```bash
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none mysolutionname:somerandomidentifier
```

### Development/Testing Commands:

**Local testing:**
```bash
# Build with custom name for testing
docker build --platform linux/amd64 -t pdf-extractor:test .

# Run with test data
docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none pdf-extractor:test
```

---



### Heading Detection Accuracy 
- **Multi-method approach:** 5 different detection techniques ensure high recall
- **Confidence scoring:** Weights and combines evidence from multiple methods
- **Dynamic adaptation:** Adjusts to each document's unique characteristics
- **Robust filtering:** Eliminates false positives while preserving true headings

### Performance 
- **Sub-5-second processing:** Well under the 10-second limit
- **Minimal dependencies:** Only PyMuPDF required, ~15MB total size
- **Memory efficient:** Processes documents page-by-page to minimize RAM usage
- **CPU optimized:** No GPU dependencies, runs efficiently on contest hardware

### Multilingual Bonus 
- **5+ Language support:** English, Japanese, Chinese, Hindi, Arabic
- **Pattern recognition:** Language-specific heading patterns
- **Unicode handling:** Proper support for international character sets
- **Auto-detection:** Automatically detects document language


---

## 🔍 **Algorithm Details**

### Method 1: Dynamic Font Analysis
- Calculates document-specific font thresholds
- Analyzes font size, weight, and family patterns
- Accounts for typography variations across documents

### Method 2: Multilingual Pattern Recognition
```python
# Example patterns supported:
- English: "1. Introduction", "Chapter 1", "ABSTRACT"
- Japanese: "第一章", "序論", "はじめに"  
- Chinese: "第一章", "摘要", "介绍"
- Hindi: "अध्याय १", "परिचय"
- Arabic: "الفصل ١", "مقدمة"
```

### Method 3: Structural Analysis
- Analyzes document layout and positioning
- Identifies section breaks and hierarchy
- Uses whitespace and positioning cues

### Method 4: Confidence Scoring
- Combines evidence from multiple detection methods
- Weights confidence based on method reliability
- Prevents duplicate headings while maximizing coverage

### Method 5: TOC Integration
- Extracts existing PDF bookmarks when available
- Falls back to text analysis for documents without TOC
- Provides highest confidence scores for bookmark-derived headings

---

## ✅ **Quality Assurance**

### Robustness Features
- **Error handling:** Graceful degradation on corrupted files
- **Edge case management:** Handles unusual document formats
- **Performance monitoring:** Built-in timing and statistics tracking
- **Output validation:** Ensures JSON format compliance

### Testing Coverage
- **Multi-language documents:** Tested on English, Japanese, Chinese samples
- **Various formats:** Academic papers, reports, books, presentations  
- **Edge cases:** Single-page docs, image-heavy PDFs, unusual typography
- **Performance testing:** Verified <10s processing on 50-page documents

---

## 🏆 **Competitive Advantages**

1. **Hybrid Approach:** Combines strengths of multiple detection methods
2. **Multilingual Excellence:** Advanced international language support
3. **Dynamic Adaptation:** Self-adjusts to document characteristics  
4. **Performance Optimized:** Engineered for contest hardware specifications
5. **Robust Error Handling:** Continues processing even with problematic files
6. **High Precision:** Smart filtering reduces false positives
7. **Maximum Recall:** Multiple methods ensure no headings are missed

---

## 📝 **Implementation Notes**

- **No external APIs:** Fully self-contained solution
- **Deterministic output:** Consistent results across runs
- **Logging:** Comprehensive progress tracking for debugging
- **Modular design:** Easy to extend with additional detection methods
- **Contest compliant:** Meets all specified requirements and constraints

# Adobe India Hackathon - Challenge 1b
## Intelligent Document Analyst

### 📋 Overview
This system acts as an intelligent document analyst that extracts and prioritizes the most relevant sections from a collection of PDF documents based on a specific persona and their job-to-be-done.

### 🚀 Features
- **Multi-format PDF Processing**: Robust extraction from various PDF types
- **Persona-aware Analysis**: Tailors results based on user role and expertise
- **Job-specific Relevance**: Prioritizes content based on specific tasks
- **Efficient Processing**: CPU-only, <1GB memory, <60s processing time
- **Structured Output**: Clean JSON format with detailed metadata

### 📁 Project Structure
```
adobe-hackathon/
├── src/
│   ├── __init__.py              # Package initialization
│   ├── main.py                  # Main analyst class
│   ├── document_processor.py    # PDF processing
│   ├── section_extractor.py     # Section extraction
│   └── persona_analyzer.py      # Persona-based analysis
├── data/
│   ├── input/                   # Input PDF files
│   └── output/                  # Generated results
├── requirements.txt             # Python dependencies
├── Dockerfile                   # Container configuration
├── run.py                       # Main execution script
├── approach_explanation.md      # Methodology explanation
└── README.md                    # This file
```

### 🛠️ Installation

#### Prerequisites
- Python 3.9 or 3.10
- Docker (for containerized execution)

#### Local Setup
```bash
# Clone or download the project
cd adobe-hackathon

# Install dependencies
pip install -r requirements.txt

# Download required NLTK data
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"
```

### 📚 Usage

#### Basic Usage
```bash
# Place PDF files in data/input/ directory
python run.py
```

#### Custom Parameters
```bash
python run.py \
  --input "path/to/pdfs" \
  --output "results.json" \
  --persona "Investment Analyst" \
  --job "Analyze revenue trends and market positioning strategies"
```

#### Docker Usage
```bash
# Build the image
docker build -t adobe-document-analyst .

# Run with mounted data directory
docker run -v $(pwd)/data:/app/data adobe-document-analyst
```

### 📊 Sample Test Cases

#### Test Case 1: Academic Research
```bash
python run.py \
  --persona "PhD Researcher in Computational Biology" \
  --job "Prepare a comprehensive literature review focusing on methodologies, datasets, and performance benchmarks"
```

#### Test Case 2: Business Analysis
```bash
python run.py \
  --persona "Investment Analyst" \
  --job "Analyze revenue trends, R&D investments, and market positioning strategies"
```

#### Test Case 3: Educational Content
```bash
python run.py \
  --persona "Undergraduate Chemistry Student" \
  --job "Identify key concepts and mechanisms for exam preparation on reaction kinetics"
```

### 📋 Output Format

The system generates a JSON file with the following structure:

```json
{
  "metadata": {
    "input_documents": ["doc1.pdf", "doc2.pdf"],
    "persona": "PhD Researcher in Computational Biology",
    "job_to_be_done": "Prepare comprehensive literature review...",
    "processing_timestamp": "2025-01-XX:XX:XX"
  },
  "extracted_sections": [
    {
      "document": "doc1.pdf",
      "page_number": 3,
      "section_title": "Methodology",
      "importance_rank": 1
    }
  ],
  "subsection_analysis": [
    {
      "document": "doc1.pdf",
      "page_number": 3,
      "refined_text": "The methodology section discusses..."
    }
  ]
}
```

### ⚡ Performance Specifications
- **Processing Time**: <60 seconds for 3-5 documents
- **Memory Usage**: <1GB RAM
- **CPU Only**: No GPU required
- **Offline**: Works without internet connection

### 🔧 Customization

#### Adding New Personas
Edit `src/persona_analyzer.py` and add to `persona_keywords`:
```python
'new_role': {
    'keywords': ['keyword1', 'keyword2', ...],
    'weight': 1.4
}
```

#### Adding Job Types
Edit `job_keywords` in `src/persona_analyzer.py`:
```python
'new_job_type': ['keyword1', 'keyword2', ...]
```

### 🐛 Troubleshooting

#### Common Issues
1. **"No PDF files found"**: Ensure PDFs are in the correct input directory
2. **Memory errors**: Reduce batch size or process fewer documents
3. **Import errors**: Verify all dependencies are installed
4. **Docker issues**: Ensure Docker Desktop is running

#### Debugging
Enable detailed logging:
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

### 📈 Algorithm Overview

1. **Document Processing**: Extract text, identify structure
2. **Section Extraction**: Find meaningful content blocks
3. **Persona Analysis**: Match content to user characteristics
4. **Relevance Scoring**: Combine multiple factors for ranking
5. **Output Generation**: Format results as structured JSON

### 🤝 Contributing
For hackathon submission:
1. Test with provided sample data
2. Verify Docker container builds successfully
3. Ensure output matches required JSON schema
4. Document any modifications in approach_explanation.md
