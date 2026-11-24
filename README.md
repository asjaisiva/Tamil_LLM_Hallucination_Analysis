# Hallucination Behaviour of Large Language Models on Tamil Questions

Dataset, code and prompts for the paper **"Hallucination Behaviour of Large Language Models on Tamil Questions: A Manually Evaluated Multi-Domain Study"**.

**Authors:** Indhumathi E, Jaisiva A S  
**Mentor:** Dr. K. Akilandeswari, Associate Professor, Government Arts College, Salem 7

## Overview

The study measures how often ten open large language models give hallucinated answers to Tamil questions. All 10,000 responses (10 models x 1,000 questions) were labeled by hand as **Correct** or **Hallucinated**.

Headline result: the overall hallucination rate ranged from 27.9% (Gemma 4 31B) to 66.9% (Phi-4 14B). See the paper for the full analysis by model, question type and domain.

## Dataset

The dataset has 1,000 Tamil questions, divided equally over five domains: Geography, History, Literature, Nature and Science (200 questions each).

| Question type | Per domain | Total |
| --- | --- | --- |
| Factual | 150 | 750 |
| True/False | 25 | 125 |
| Semantically incorrect | 25 | 125 |
| **Total** | **200** | **1,000** |

- **Sources:** about 99% of the source text comes from Tamil Wikipedia, and the rest from the 2024 edition of the 10th Standard Samacheer Kalvi Science textbook. All questions were written in Tamil from Tamil source text, not translated.
- **Generation:** candidate questions were generated with GPT, Gemini Pro and Claude Sonnet, then reviewed manually. Only relevant questions that suited their type were kept.
- **Topics:** the topics behind the 750 factual questions are listed in Appendix C of the paper.
- **File format:** Excel files with the columns `S No`, `Question` and `Answer`, which is the format the evaluation notebook reads.

## Models evaluated

| Model | Parameters | Platform |
| --- | --- | --- |
| Tamilan-2 | 27B | Kaggle |
| Gemma 2 | 27B | Kaggle |
| Gemma 3 | 12B | Colab |
| Gemma 3 | 27B | Kaggle |
| Gemma 4 | 12B | Colab |
| Gemma 4 | 26B | Kaggle |
| Gemma 4 | 31B | Kaggle |
| Phi-4 | 14B | Colab |
| Llama 3.1 | 8B | Colab |
| TamilLlama 2 | 8B | Colab |

All models were run through [Ollama](https://ollama.com). The Ollama tags and software versions are listed in Appendix B of the paper.

## Repository structure

```
.
├── README.md
├── LICENSE
├── data/       questions with reference answers
├── code/       Ollama evaluation notebook
└── prompts/
    ├── evaluation_prompts.md   prompts used to query the models
    └── generation_prompts.md   prompts used to generate the questions
```

## How to reproduce the evaluation

1. Open the notebook in `code/` in Google Colab and select a GPU runtime (the notebook was run on a T4).
2. Upload a question file from `data/` to `/content/`.
3. In the settings cell, set `MODEL` to the Ollama tag of the model and `DATASET` to the path of the question file.
4. Run the notebook. When it asks, enter `1` for factual, `2` for true/false or `3` for semantically incorrect questions, so that the matching prompt from `prompts/evaluation_prompts.md` is used.
5. Responses are saved as an Excel file in `/content/results/`, named after the dataset file and the model.

Settings used for all models: temperature 0.4, seed 42, at most 1,000 new tokens, one response per question. Each question is sent as a separate single-turn request. A checkpoint is saved every 25 questions, and the Ollama server is restarted every 40 questions to keep memory use down on free-tier GPUs.

Responses were then labeled manually by two native Tamil speakers against reference answers, as described in the paper.

