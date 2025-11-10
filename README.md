# Prompting with Amazon Bedrock Models — Course Notes & Examples

This repository contains course materials and practical guides about prompt engineering and working with large language models (LLMs), with a focus on techniques useful when interacting with Amazon Bedrock and other modern LLMs.

This README provides a concise map of the repository, short descriptions of each file, recommended workflows for using the materials, and suggestions for next steps.

---

## Table of contents

- [Repository overview](#repository-overview)  
- [Files and descriptions](#files-and-descriptions)  
- [How to use these materials](#how-to-use-these-materials)  
  - [Viewing the notebook](#viewing-the-notebook)  
  - [Reading the lessons (markdown files)](#reading-the-lessons-markdown-files)  
- [Suggested exercises and workflows](#suggested-exercises-and-workflows)  
- [Contributing & editing notes](#contributing--editing-notes)  
- [License](#license)

---

## Repository overview

This collection of lessons is designed to teach prompt engineering fundamentals, best practices for producing parsable outputs (JSON/YAML/HTML), reasoning and chain-of-thought techniques, and practical tips for generating runnable code with LLMs. It also covers debugging workflows, handling context windows, iterative prompting, and fetching context from files.

---

## Files and descriptions

- [README.md](README.md) — This file.
- [Understanding-LLMs.ipynb](Understanding-LLMs.ipynb) — Jupyter notebook with foundational lessons on how LLMs generate text, context windows, reasoning techniques, and editing messages to refine responses. Open with Jupyter or VS Code's notebook viewer.
- [Prompting-Foundations.md](Prompting-Foundations.md) — Introductory lessons on structuring prompts, model-specific formatting (XML/Markdown), constraints, and using examples.
- [Diving-Deep-Into-Prompt-Engineering.md](Diving-Deep-Into-Prompt-Engineering.md) — Advanced prompt-engineering techniques: highlighting instructions, consequences/rewards, system prompts, iterative prompting, and the generated knowledge method.
- [Parsing-Data-with-LLMs.md](Parsing-Data-with-LLMs.md) — Practical guidance for building prompts that parse structured data, produce runnable code (Python), and debugging strategies when using LLMs for data tasks.
- [Solving-Real-Challenges-with-AWS-Bedrock-Models.md](Solving-Real-Challenges-with-AWS-Bedrock-Models.md) — Examples and patterns for getting parsable outputs, placeholders, explanations in examples, and producing clean runnable code for non-technical users.

Each file is written as a lesson; read them in sequence for the best learning flow:
1. [Prompting-Foundations.md](Prompting-Foundations.md)  
2. [Understanding-LLMs.ipynb](Understanding-LLMs.ipynb)  
3. [Diving-Deep-Into-Prompt-Engineering.md](Diving-Deep-Into-Prompt-Engineering.md)  
4. [Parsing-Data-with-LLMs.md](Parsing-Data-with-LLMs.md)  
5. [Solving-Real-Challenges-with-AWS-Bedrock-Models.md](Solving-Real-Challenges-with-AWS-Bedrock-Models.md)

---

## How to use these materials

### Viewing the notebook
- Open [Understanding-LLMs.ipynb](Understanding-LLMs.ipynb) in:
  - VS Code (built-in notebook renderer) or
  - Jupyter Notebook / JupyterLab.
- Run cells interactively to annotate or experiment with examples.
- Use the notebook for hands-on exploration of tokenization, context windows, CoT prompts, and demonstration snippets.

### Reading the lessons (markdown files)
- Each lesson is a standalone Markdown file. Open them in VS Code or any Markdown viewer.
- Examples inside the lessons often show prompt templates and constraints. Copy those templates into your development environment and adapt them for your target model (Bedrock, Claude, GPT-family, etc.).

---

## Suggested exercises and workflows

1. Start with the notebook ([Understanding-LLMs.ipynb](Understanding-LLMs.ipynb)) to internalize token-level generation and context behavior.
2. Practice structuring prompts using [Prompting-Foundations.md](Prompting-Foundations.md) templates.
3. Use the "generated knowledge method" from [Diving-Deep-Into-Prompt-Engineering.md](Diving-Deep-Into-Prompt-Engineering.md) for multi-step tasks (explain → request).
4. Build prompts that produce parsable outputs (JSON/YAML) following patterns in [Solving-Real-Challenges-with-AWS-Bedrock-Models.md](Solving-Real-Challenges-with-AWS-Bedrock-Models.md).
5. Try the data parsing examples from [Parsing-Data-with-LLMs.md](Parsing-Data-with-LLMs.md) and run the generated Python scripts locally after reviewing for safety.

Practical tip: Always instruct LLMs to "Provide ONLY the output" when you need machine-parsable results. Use placeholders and explicit constraints to reduce hallucination and formatting drift.

