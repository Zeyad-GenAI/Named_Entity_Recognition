<img width="1279" height="668" alt="NER for Sample 1" src="https://github.com/user-attachments/assets/f11f0682-93b7-49b8-8eb5-ea9b5a4bcee1" /># 🔍 NER Comparison Tool: Advanced Named Entity Recognition Analysis

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/)
[![SpaCy](https://img.shields.io/badge/SpaCy-3.0%2B-09a3d5.svg)](https://spacy.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

> **A comprehensive Named Entity Recognition analysis tool that compares rule-based approaches with state-of-the-art SpaCy models for multilingual NER tasks.**

## 📋 Overview

This project provides a robust framework for analyzing and comparing different Named Entity Recognition (NER) approaches on CoNLL-2003 datasets. It offers side-by-side comparisons between rule-based methods and advanced SpaCy models, complete with visual highlighting and detailed performance analysis.

### 🎯 Why This Tool Matters

- **Educational**: Perfect for understanding NER fundamentals and model differences
- **Research-Oriented**: Facilitates comparative analysis between different NER approaches
- **Production-Ready**: Can be adapted for real-world NER applications
- **Visualization**: Provides clear, color-coded entity highlighting for better insights

---

## ✨ Key Features

### 🧠 Multiple NER Approaches
- **Rule-Based NER**: Custom pattern matching for entities
- **SpaCy Small Model**: Fast, lightweight `en_core_web_sm`
- **SpaCy Large Model**: High-accuracy `en_core_web_lg`

### 📊 Advanced Analysis Tools
- **Visual Entity Highlighting**: Color-coded entity display in terminal
- **Interactive Visualization**: Built-in SpaCy displaCy integration
- **Comparative Analysis**: Side-by-side model performance tables
- **CoNLL Dataset Support**: Native parsing for CoNLL-2003 format

### 🎨 Enhanced User Experience
- **Google Colab Integration**: Ready-to-run notebook environment
- **Pandas DataFrames**: Organized comparison results in tabular format
- **Customizable Samples**: Adjustable dataset sample sizes
- **Professional Output**: Clean, formatted results with color-coded highlighting
- **Interactive Visualization**: Built-in SpaCy displaCy entity visualization

---

## 🛠️ Prerequisites

### System Requirements
- **Python**: 3.7 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended for large model)
- **Storage**: ~500MB for models and dependencies

### Required Libraries
```python
spacy>=3.0.0
pandas>=1.3.0
google-colab  # For Colab environment
```

### Language Models
- `en_core_web_sm` - English small model (~15MB)
- `en_core_web_lg` - English large model (~750MB)

---

## 🚀 Installation & Setup

### Option 1: Google Colab (Recommended)
```python
# Install dependencies
!pip install -q spacy pandas
!python -m spacy download en_core_web_sm
!python -m spacy download en_core_web_lg
```

### Option 2: Local Environment
```bash
# Clone the repository
git clone https://github.com/yourusername/ner-comparison-tool.git
cd ner-comparison-tool

# Create virtual environment
python -m venv ner_env
source ner_env/bin/activate  # On Windows: ner_env\Scripts\activate

# Install dependencies
pip install spacy pandas
python -m spacy download en_core_web_sm
python -m spacy download en_core_web_lg
```

---

## 📖 Usage Guide

### Quick Start
1. **Mount Google Drive** (Colab only):
```python
from google.colab import drive
drive.mount('/content/drive')
```

2. **Prepare Your Dataset**:
   - Upload CoNLL-2003 format file to your Drive
   - Update the `train_path` variable with your file location

3. **Run Analysis**:
```python
# Load and parse dataset
samples = parse_conll(train_path, num_sentences=3)

# Process samples with all NER methods
for idx, text in enumerate(samples):
    # Rule-based analysis
    rule_entities = rule_based_ner(text)
    
    # SpaCy model analysis
    sm_entities, sm_doc = spacy_ner(text, 'en_core_web_sm')
    lg_entities, lg_doc = spacy_ner(text, 'en_core_web_lg')
```

### Advanced Configuration
```python
# Customize number of sentences to process
samples = parse_conll(train_path, num_sentences=10)

# Modify entity types for rule-based NER
def custom_rule_based_ner(text):
    # Add your custom patterns here
    pass
```

### Sample Output

#### Example 1: Political Text Analysis
```
=== NER for Sample 1 ===

Rule-based Entities: [('German', 'PER'), ('British', 'PER')]
Highlighted (Rule-based):
EU rejects German (PER) call to boycott British (PER) lamb .

en_core_web_sm Entities: [('EU', 'ORG'), ('German', 'NORP'), ('British', 'NORP')]
Highlighted (sm):
EU (ORG) rejects German (NORP) call to boycott British (NORP) lamb .

en_core_web_lg Entities: [('EU', 'ORG'), ('German', 'NORP'), ('British', 'NORP')]
Highlighted (lg):
EU (ORG) rejects German (NORP) call to boycott British (NORP) lamb .
```

#### Example 2: Person Name Recognition
```
=== NER for Sample 2 ===

Rule-based Entities: [('Peter Blackburn', 'PER')]
Highlighted (Rule-based):
Peter Blackburn (PER)

en_core_web_sm Entities: [('Peter Blackburn', 'PERSON')]
Highlighted (sm):
Peter Blackburn (PERSON)

en_core_web_lg Entities: [('Peter Blackburn', 'PERSON')]
Highlighted (lg):
Peter Blackburn (PERSON)
```

#### Example 3: Location and Date Recognition
```
=== NER for Sample 3 ===

Rule-based Entities: []
Highlighted (Rule-based):
BRUSSELS 1996-08-22

en_core_web_sm Entities: [('BRUSSELS', 'GPE'), ('1996-08-22', 'DATE')]
Highlighted (sm):
BRUSSELS (GPE) 1996-08-22 (DATE)

en_core_web_lg Entities: [('BRUSSELS', 'GPE'), ('1996-08-22', 'DATE')]
Highlighted (lg):
BRUSSELS (GPE) 1996-08-22 (DATE)
```

### Visual Entity Highlighting

The tool provides color-coded entity highlighting:
- 🟢 **Green**: Person entities (PER/PERSON)
- 🔵 **Blue**: Organization entities (ORG)
- 🟡 **Yellow**: Location entities (LOC/GPE)
- 🟠 **Orange**: Nationality/Political entities (NORP)
- 🔄 **Cyan**: Date entities (DATE)

### 📊 Analysis Results & Visual Output

#### Sample Results with Visual Highlighting

**Sample 1: Political Text Analysis**

![NER Sample 1 Results]<img width="1279" height="668" alt="NER for Sample 1" src="https://github.com/user-attachments/assets/f11f0682-93b7-49b8-8eb5-ea9b5a4bcee1" />

```
Text: "EU rejects German call to boycott British lamb"
```

**Sample 2: Person Name Recognition**

![NER Sample 2 Results]<img width="1279" height="668" alt="NER for Sample 2" src="https://github.com/Zeyad-GenAI/Named_Entity_Recognition/blob/c9bff27a7ce0bf8c8934a42da7314ae1295270c9/results/NER%20for%20Sample%202.png" />

```
Text: "Peter Blackburn"
```

**Sample 3: Location and Date Recognition**

![NER Sample 3 Results]<img width="1279" height="668" alt="NER for Sample 3" src="https://github.com/Zeyad-GenAI/Named_Entity_Recognition/blob/c9bff27a7ce0bf8c8934a42da7314ae1295270c9/results/NER%20for%20Sample%203.png" />

```
Text: "BRUSSELS 1996-08-22"
```

#### Detailed Comparison Results

**📊 Sample 1 Analysis:**
```
Text: "EU rejects German call to boycott British lamb"
┌─────────────────────┬────────────────────┬─────────────────────────────────┐
│ Method              │ Entities Found     │ Classification                  │
├─────────────────────┼────────────────────┼─────────────────────────────────┤
│ Rule-based          │ German, British    │ Both as PER (incorrect)         │
│ en_core_web_sm      │ EU, German, British│ ORG, NORP, NORP (correct)      │
│ en_core_web_lg      │ EU, German, British│ ORG, NORP, NORP (correct)      │
└─────────────────────┴────────────────────┴─────────────────────────────────┘
```

**📊 Sample 2 Analysis:**
```
Text: "Peter Blackburn"
┌─────────────────────┬────────────────────┬─────────────────────────────────┐
│ Method              │ Entities Found     │ Classification                  │
├─────────────────────┼────────────────────┼─────────────────────────────────┤
│ Rule-based          │ Peter Blackburn    │ PER (correct concept)           │
│ en_core_web_sm      │ Peter Blackburn    │ PERSON (correct)                │
│ en_core_web_lg      │ Peter Blackburn    │ PERSON (correct)                │
└─────────────────────┴────────────────────┴─────────────────────────────────┘
```

**📊 Sample 3 Analysis:**
```
Text: "BRUSSELS 1996-08-22"
┌─────────────────────┬────────────────────┬─────────────────────────────────┐
│ Method              │ Entities Found     │ Classification                  │
├─────────────────────┼────────────────────┼─────────────────────────────────┤
│ Rule-based          │ None               │ Failed to detect entities       │
│ en_core_web_sm      │ BRUSSELS, 1996-08-22│ GPE, DATE (correct)           │
│ en_core_web_lg      │ BRUSSELS, 1996-08-22│ GPE, DATE (correct)           │
└─────────────────────┴────────────────────┴─────────────────────────────────┘
```

#### Key Observations
- **Rule-based limitations**: Often misclassifies nationalities as persons
- **SpaCy consistency**: Both SM and LG models show high agreement
- **Entity type accuracy**: SpaCy models better distinguish between PERSON, NORP, and GPE
- **Date recognition**: Only SpaCy models successfully identify date patterns

---

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### Getting Started
1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** your changes: `git commit -m 'Add amazing feature'`
4. **Push** to the branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

### Contribution Guidelines
- Follow PEP 8 style guidelines
- Add unit tests for new features
- Update documentation for any API changes
- Ensure all tests pass before submitting PR

### Areas for Contribution
- 🌐 **Multilingual Support**: Add support for other languages
- 🧪 **New Models**: Integrate additional NER models
- 📊 **Metrics**: Add precision, recall, and F1-score calculations
- 🎨 **Visualization**: Enhance output formatting and charts

---

## 📈 Performance Benchmarks

| Model | Speed | Memory | Accuracy | Best Use Case |
|-------|-------|---------|----------|---------------|
| Rule-Based | ⚡⚡⚡ | 💾 | ⭐⭐ | Quick prototyping |
| en_core_web_sm | ⚡⚡ | 💾💾 | ⭐⭐⭐ | Production apps |
| en_core_web_lg | ⚡ | 💾💾💾 | ⭐⭐⭐⭐ | High accuracy needs |

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 NER Comparison Tool Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files...
```

---

## 🙏 Acknowledgements

### Core Technologies
- **[SpaCy](https://spacy.io/)** - Industrial-strength Natural Language Processing
- **[pandas](https://pandas.pydata.org/)** - Powerful data analysis toolkit
- **[Google Colab](https://colab.research.google.com/)** - Collaborative notebook environment

### Datasets
- **[CoNLL-2003](https://www.clips.uantwerpen.be/conll2003/ner/)** - Named Entity Recognition shared task dataset

### Inspiration
- Research papers in Named Entity Recognition
- SpaCy community tutorials and examples
- Open source NLP community contributions

### Special Thanks
- Contributors who helped improve the codebase
- Beta testers who provided valuable feedback
- The broader NLP research community

---

<div align="center">

**⭐ Star this repository if you find it helpful!**


</div>
