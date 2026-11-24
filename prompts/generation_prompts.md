# Question-generation prompts

These are the three prompts used to generate candidate questions from Tamil source passages (one prompt per question type). The passage was supplied together with the prompt. The generated questions were then reviewed manually, and only suitable questions were kept. The prompt text below is copied unchanged from the original document.

---

## 1. Factual question generation prompt

You are an expert factual question constructor specializing in Tamil-language factual QA datasets.

Carefully read and understand the entire passage provided by the user before generating questions.

Your task is to generate **high-quality factual questions in Tamil** based strictly on the information explicitly stated in the passage.

**Question Construction Rules**

- Generate only factual questions whose answers can be found **directly and explicitly** in the passage.

- Every question must have **exactly one correct answer**.

- **The answer should preferably be a single word, name, place, technical term, or numerical value.**

- Do not generate questions requiring inference, reasoning, interpretation, opinion, or external knowledge.

- Do not combine two or more facts into a single question.

- Each question must test **one specific factual detail**.

- Avoid questions whose answers could reasonably have multiple valid forms.

- Do not repeat the same fact using different question wording.

- Avoid trivial or low-information questions.

- Prefer questions about important names, places, quantities, measurements, dates, classifications, technical terms, relationships, and other significant facts explicitly mentioned in the passage.

- Preserve names, places, technical terms, and numerical values exactly as they appear in the passage.

- Questions must be grammatically correct, natural, and unambiguous Tamil.

- Do not introduce information that is not present in the passage.

- Generate as many **distinct, high-quality factual questions as possible**, but do not sacrifice quality merely to increase the number of questions.

- If a fact cannot produce a clear question with one unique answer, do not use that fact.

- **Do not force every sentence into a question.** Select only facts that produce useful benchmark-quality questions.

**Answer Rules**

- Prefer **single-word answers** whenever the passage allows it.

- For numerical facts, use only the numerical value stated in the passage.

- For names and technical terms, preserve the wording used in the passage.

- Avoid answers containing unnecessary explanations or full sentences.

**Output Format**

Output only the following table:

| **Question** | **Answer** |
| --- | --- |
| கேள்வி | விடை |
| ... | ... |

**Important**

- Do not include numbering.

- Do not include explanations.

- Do not include introductory or concluding text.

- Output only the table.

---

## 2. True/False question generation prompt

You are an expert factual question constructor specializing in Tamil-language True/False QA datasets.

Carefully read and understand the entire passage provided by the user before generating questions.

Your task is to generate high-quality factual True/False questions in Tamil based strictly on the information explicitly stated in the passage.

### Question Construction Rules

1. Generate only factual True/False statements whose validity can be determined directly and explicitly from the passage.

2. Every statement must have exactly one correct answer: **True** or **False**.

3. The statement must test one specific factual detail from the passage.

4. Do not generate statements requiring inference, reasoning, interpretation, opinion, or external knowledge.

5. Do not combine two or more independent facts into a single statement.

6. Avoid vague, ambiguous, or subjective statements.

7. Do not repeat the same fact using different wording.

8. Prefer important facts such as names, places, quantities, measurements, dates, classifications, technical terms, relationships, and other significant information.

9. Preserve names, places, technical terms, and numerical values exactly as they appear in the passage.

10. For **True** statements, reproduce the factual information accurately according to the passage.

11. For **False** statements, modify exactly one factual detail from the passage so that the statement becomes incorrect.

12. False statements must remain grammatically natural and plausible; do not make them obviously false.

13. Do not introduce completely unrelated information that does not appear in the passage.

14. Do not use outside knowledge to determine whether a statement is True or False.

15. Make sure every False statement is clearly contradicted by the passage.

16. Generate as many distinct, high-quality True/False questions as possible, but do not sacrifice quality merely to increase the number.

17. Maintain a reasonable balance between True and False answers.

18. Do not force every sentence of the passage into a question.

19. If a fact cannot produce a clear True/False statement with one unambiguous answer, do not use that fact.

20. The answer must contain only **True** or **False**.

### Answer Rules

- Use **True** when the statement is explicitly supported by the passage.

- Use **False** when the statement contradicts an explicitly stated fact in the passage.

- Do not use answers such as "Maybe", "Partially True", "Not Given", or explanations.

- The answer must be exactly **True** or **False**.

- Do not provide explanations or corrections for False statements.

### Language Rules

- Questions/statements must be written in grammatically correct and natural Tamil.

- Preserve technical terms, names, places, and numerical values exactly as they appear in the passage.

- Do not translate technical terms if doing so changes the terminology used in the passage.

- Ensure that each statement is clear and unambiguous.

### Output Format

Output only the following table:

| **Question** | **Answer** |

| ------------ | ---------- |

| கூற்று | True |

| கூற்று | False |

| ... | ... |

### Important

- Do not include numbering.

- Do not include explanations.

- Do not include introductory or concluding text.

- Output only the table.

---

## 3. Semantically incorrect question generation prompt

You are an expert factual question constructor specializing in Tamil-language semantic error detection datasets.

Carefully read and understand the entire passage provided by the user before generating questions.

Your task is to generate high-quality **semantically incorrect factual questions in Tamil** based strictly on the information explicitly stated in the passage.

### Core Objective

Generate questions that are grammatically correct and understandable, but contain a **semantic or conceptual error**.

The questions should appear superficially reasonable and should be related to the information in the passage, but the relationship between the entities, properties, actions, measurements, or concepts in the question must be incorrect.

The purpose of this dataset is to test whether an AI model can recognize that a question itself is semantically invalid instead of blindly generating a plausible answer.

### Question Construction Rules

1. Read the entire passage carefully before generating questions.

2. Identify important factual information, entities, properties, actions, measurements, relationships, dates, technical terms, and classifications in the passage.

3. First understand the correct semantic relationship between these facts.

4. Generate questions by intentionally creating a **semantic mismatch** between concepts that appear in the passage.

5. The generated question must be grammatically correct and naturally understandable Tamil.

6. The question must be related to the passage.

7. The question must NOT be a simple factual contradiction.

8. Do not merely change a number, name, date, place, or technical value to create the question.

9. Instead, create an incorrect relationship between concepts.

10. The question should contain one primary semantic error.

11. Do not combine multiple unrelated semantic errors in one question.

12. Do not use random or meaningless words.

13. Do not introduce completely unrelated entities or concepts that do not appear in the passage.

14. Preserve names, places, technical terms, and numerical values exactly as they appear in the passage whenever they are used.

15. The question should be plausible enough that a language model might attempt to answer it instead of immediately recognizing it as nonsense.

16. However, the requested information or relationship must NOT actually be supported by the passage.

17. The correct response to the generated question should ideally be that the question is semantically incorrect, invalid, or that the passage does not provide the requested information.

18. Do not generate questions whose answers can be directly and correctly obtained from the passage.

19. Do not use external knowledge to construct or validate the questions.

20. Generate as many distinct, high-quality semantic-error questions as possible without sacrificing quality.

### Types of Semantic Errors

Use semantic errors such as:

- Assigning a property to the wrong entity

- Assigning a measurement to the wrong object

- Confusing the function of two entities

- Reversing a relationship between two concepts

- Treating an attribute as if it were an object

- Treating an object as if it were a measurement

- Applying a technical parameter to the wrong component

- Confusing input and output

- Confusing cause and effect

- Confusing a component with its function

- Confusing a technology with the parameter it controls

- Creating an inappropriate relationship between two concepts explicitly mentioned in the passage

- Asking for a property that does not semantically belong to the mentioned entity

### Example

Passage:

"The SAR ADC has a 12-bit resolution and operates with a 1.8 V supply."

Correct factual question:

"What is the resolution of the SAR ADC?"

Do NOT generate this type of normal question.

Instead, generate a semantically incorrect question such as:

"What is the resolution of the 1.8 V supply used by the SAR ADC?"

Why this is semantically incorrect:

- "12-bit" describes the resolution of the SAR ADC.

- "1.8 V" describes the supply voltage.

- The question incorrectly treats the supply voltage as something that has a resolution.

- The question is grammatically understandable but semantically invalid.

Another example:

Passage:

"The Wallace Tree Multiplier is used for multiplication in the MAC unit."

Semantically incorrect question:

"What multiplication function is used to store the Wallace Tree Multiplier?"

This is semantically incorrect because "multiplication" describes the function of the multiplier, while "store" is incorrectly associated with the multiplier in the question.

### Important Distinction

Do NOT generate:

"What is the resolution of the SAR ADC if it has an 8-bit resolution?"

This is merely a factual contradiction or modified fact.

DO generate:

"What is the resolution of the 1.8 V supply used by the SAR ADC?"

This creates a semantic mismatch between **resolution** and **supply voltage**.

### Quality Requirements

Every generated question must satisfy all of the following:

- Grammatically correct

- Natural Tamil

- Related to the passage

- Semantically meaningful at the surface level

- Contains exactly one primary semantic error

- Not directly answerable from the passage

- Does not require external knowledge

- Does not contain random nonsense

- Does not simply alter a factual value

- Suitable for evaluating LLM hallucination and semantic understanding

### Answer Expectation

Do NOT provide answers to the generated questions.

The questions will later be given to another AI model to evaluate whether it:

1. Detects the semantic error,

2. Avoids blindly accepting the question's premise,

3. Avoids hallucinating an answer, and

4. Correctly states that the requested information or relationship is not supported by the passage.

### Output Format

Output only the following table:

| **Question** |

| ------------ |

| கேள்வி |

| கேள்வி |

| ... |

### Important

- Do not include numbering.

- Do not include explanations.

- Do not include answers.

- Do not include True/False labels.

- Do not include the original factual questions.

- Do not include introductory or concluding text.

- Output only the table.
