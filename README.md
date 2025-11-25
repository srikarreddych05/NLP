 ADE–SUD NLP Pipeline  
A Complete End-to-End System for Extracting Adverse Drug Events Using Deep Learning  
Technologies: BioBERT, BERT, HuggingFace Transformers, Token Classification, Relation Extraction, Python  
Dataset: ADE Corpus v2 (HuggingFace)

This project implements a full biomedical NLP pipeline for extracting Adverse Drug Events (ADEs) and detecting *Substance Use / Misuse (SUD)* from free-text data.

The pipeline performs:

1. **Document-Level Classification**  
   Predicts whether a text is:
   - `ADE`
   - `SUD` (drug abuse/misuse/overdose)
   - `Irrelevant`

2. **Named Entity Recognition (NER)**  
   Extracts:
   - `DRUG` entities  
   - `ADE` (Adverse Event) entities  

3. **Relation Extraction (RE)**  
   Determines whether a detected **Drug → ADE** pair is a **causal relationship**.

4. **End-to-End Pipeline**  
   A single function that processes raw text and returns structured JSON containing:
   - Classification label  
   - Extracted entities  
   - Drug–ADE causal links  

This project uses **BioBERT**, **BERT-base**, and **ADE Corpus v2**, along with generated synthetic data for SUD and Irrelevant classes.

---

## 🎯 Project Goals

✔ Build a scalable ADE extraction system  
✔ Identify harmful drug effects from textual data  
✔ Use medical domain BERT models for high accuracy  
✔ Create fully automated training + inference pipelines  
✔ Provide transparent, well-structured, reproducible code  

---

## 🏗️ Pipeline Architecture

### 🔹 1. Unified Classifier (BioBERT)
- Input: Raw text  
- Output: ADE / SUD / Irrelevant  
- Purpose: Reduce downstream computation (NER + RE only for ADE texts)

### 🔹 2. NER (BioBERT Token Classification)
- Labels: `B-DRUG`, `I-DRUG`, `B-ADE`, `I-ADE`, `O`  
- Extracts the drug and adverse event spans from the text

### 🔹 3. Relation Extraction (RE)
- Model: BERT pair classifier  
- Input: `(drug, adverse_event)`  
- Output: `CAUSES` or `NOT_CAUSAL`

### 🔹 4. Full Pipeline
Combines all components:

