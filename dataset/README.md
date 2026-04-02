# maritime_legal_translation_evaluation_dataset

## Overview

This dataset contains 2,000 Chinese-English bilingual sentence pairs from maritime legal documents, designed for evaluating large language models (LLMs) translation performance in specialized legal domains.

## Dataset Statistics

- **Total Sentence Pairs**: 2,000
- **Chinese-to-English**: 1,000 sentence pairs
- **English-to-Chinese**: 1,000 sentence pairs
- **Large Language Models**: 8 representative models
- **Domain**: Maritime legal documents

## File Structure

```
maritime_legal_translation_evaluation_dataset/
├── C2E/
│   ├── C2E_translations/
│   │   ├── Claude-3.5 Sonnet.txt
│   │   ├── ERINE Bot(4.0).txt
│   │   ├── GLM-4.txt
│   │   ├── GPT-4o.txt
│   │   ├── Gemini 1.5 Pro.txt
│   │   ├── HunyuanAide.txt
│   │   ├── Kimi.txt
│   │   └── TowerInstruct-7B.txt
│   ├── reference.txt
│   └── source.txt
└── E2C/
    ├── E2C_translations/
    │   ├── Claude-3.5 Sonnet.txt
    │   ├── ERINE Bot(4.0).txt
    │   ├── GLM-4.txt
    │   ├── GPT-4o.txt
    │   ├── Gemini 1.5 Pro.txt
    │   ├── HunyuanAide.txt
    │   ├── Kimi.txt
    │   └── TowerInstruct-7B.txt
    ├── reference.txt
    └── source.txt
```

## Contents

- Source sentences in both Chinese and English
- Reference translations for both directions
- Generated translations from 8 LLMs for all sentence pairs
- Complete translation outputs for bidirectional evaluation

## Usage

This dataset supports comprehensive bidirectional translation evaluation using automated metrics such as BERTScore, BLEURT, and COMET.
