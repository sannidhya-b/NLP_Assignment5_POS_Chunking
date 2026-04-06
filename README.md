# 🤖 NLP Assignment 5 — Fine-Tuning BERT for POS Tagging & Chunking
### Data Science Internship — February 2026

---

## 👩‍💻 Intern Details
| Field | Details |
|-------|---------|
| **Intern ID** | IN226066402 |
| **Name** | Sannidhya Bahulekar |
| **Assignment** | NLP Assignment 5 — Token Classification |
| **Task** | Fine-Tuning BERT/DistilBERT for POS Tagging & Chunking |

---

## 📌 Objective
Build and fine-tune a transformer model **(DistilBERT)** to perform:
- **POS Tagging** — Assign grammatical tags (Noun, Verb, Adjective, etc.) to each word
- **Chunking** — Group words into meaningful phrases (NP, VP, PP, etc.)

---

## 🛠️ Tools & Technologies
| Tool | Purpose |
|------|---------|
| Python | Programming language |
| Hugging Face Transformers | Pre-trained models & Trainer API |
| PyTorch | Deep learning framework |
| Datasets (HuggingFace) | Load CoNLL-2003 dataset |
| Seqeval | Sequence evaluation metrics |
| spaCy | POS tagging comparison |
| Google Colab | Training environment (GPU) |

---

## 📂 File Structure
```
NLP_Assignment5/
└── NLP_Assignment5_POS_Chunking.ipynb   ← Main notebook
```

---

## 📊 Dataset
| Property | Details |
|----------|---------|
| **Name** | CoNLL-2003 |
| **Source** | Hugging Face Datasets Hub |
| **Train Samples** | 14,041 |
| **Validation Samples** | 3,250 |
| **Test Samples** | 3,453 |
| **POS Tag Labels** | 47 unique tags |
| **Chunk Tag Labels** | 23 unique tags |

### Chunk Tag Categories:
```
O, B-ADJP, I-ADJP, B-ADVP, I-ADVP, B-CONJP, I-CONJP,
B-INTJ, I-INTJ, B-LST, I-LST, B-NP, I-NP, B-PP, I-PP,
B-PRT, I-PRT, B-SBAR, I-SBAR, B-UCP, I-UCP, B-VP, I-VP
```

---

## 🧠 Model Details
| Property | Details |
|----------|---------|
| **Base Model** | distilbert-base-uncased |
| **Task** | Token Classification (Chunking) |
| **Total Parameters** | ~66 Million |
| **Fine-tuned on** | CoNLL-2003 |

---

## ⚙️ Training Configuration
| Parameter | Value |
|-----------|-------|
| Epochs | 3 |
| Batch Size | 16 |
| Learning Rate | 2e-5 |
| Weight Decay | 0.01 |
| Max Sequence Length | 128 |
| Evaluation Strategy | Per Epoch |

---

## 📈 Evaluation Results
| Metric | Score |
|--------|-------|
| **Precision** | ~93% |
| **Recall** | ~93% |
| **F1 Score** | ~93% |
| **Accuracy** | ~97% |

---

## 🔍 Inference Example

**Input Sentence:**
```
John works at Google in California
```

**Output:**
| Word | POS Tag | Chunk Tag |
|------|---------|-----------|
| John | PROPN | B-NP |
| works | VERB | B-VP |
| at | ADP | B-PP |
| Google | PROPN | B-NP |
| in | ADP | B-PP |
| California | PROPN | B-NP |

---

## 📋 Task Breakdown
| Task | Description | Weight |
|------|-------------|--------|
| Task 1 | Dataset Selection — CoNLL-2003 | 10% |
| Task 2 | Data Preprocessing — Tokenization & Label Alignment | 15% |
| Task 3 | Model Setup — DistilBERT with id2label mapping | 15% |
| Task 4 | Training — Hugging Face Trainer API | 20% |
| Task 5 | Evaluation — Precision, Recall, F1 using seqeval | 15% |
| Task 6 | Inference — Custom sentence predictions | 10% |
| Task 7 | Comparison — POS Tagging vs Chunking | 10% |
| Task 8 | Report — Challenges & Observations | 5% |

---

## 🔄 Pipeline Flow
```
Raw Data → Tokenization → Label Alignment → Model Training → Evaluation → Inference → Comparison
```

---

## 📝 POS Tagging vs Chunking

| Feature | POS Tagging | Chunking |
|---------|-------------|----------|
| **Level** | Word-level | Phrase-level |
| **Output** | One tag per word | BIO tags (B-, I-, O) |
| **Example** | `John → PROPN` | `John → B-NP` |
| **Complexity** | Easier | Medium |
| **Use case** | Grammar analysis | Phrase extraction |

---

## ⚠️ Key Challenges
1. **Subword Tokenization** — BERT splits words into subwords; labels must be aligned using `word_ids()`
2. **Special Tokens** — `[CLS]` and `[SEP]` are assigned `-100` to be ignored during training
3. **Label Imbalance** — The `O` (Outside) tag dominates the dataset
4. **Training Time** — Fine-tuning requires GPU for reasonable speed

---

## 🚀 How to Run


### Option 1 — Local Setup
```bash
# Install dependencies
pip install transformers datasets seqeval torch spacy
python -m spacy download en_core_web_sm

# Open notebook
jupyter notebook NLP_Assignment5_POS_Chunking.ipynb
```
### Option 2 — Google Colab 
1. Open [Google Colab](https://colab.research.google.com)
2. Click **File → Upload Notebook**
3. Upload `NLP_Assignment5_POS_Chunking.ipynb`
4. Go to **Runtime → Change runtime type → GPU**
5. Run all cells with **Shift + Enter**

---

*Built for Data Science Internship — February 2026 · NLP Assignment 5 🚀*
