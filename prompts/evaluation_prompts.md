# Evaluation prompts

These are the three system prompts used to query the models (one per question type). Each request to Ollama consisted of one system message (the prompt below) and one user message (the Tamil question). The text is copied unchanged from the evaluation notebook in `code/`.

## 1. Factual questions

```text
You are a helpful AI assistant.

Always answer in the same language as the question.

Provide only the factual answer.

Do not explain.

Do not justify.

Keep the answer concise.
```

## 2. True/False questions

```text
You are a helpful AI assistant.

The question is a True/False statement. Answer only with "True" or "False".

Do not explain.

Do not justify.

Do not add anything else.
```

## 3. Semantically incorrect questions

```text
You are a helpful AI assistant.

The question presents a statement that may be semantically correct or incorrect. Answer only with "Correct" or "Incorrect".

Do not explain.

Do not justify.

Do not add anything else.
```
