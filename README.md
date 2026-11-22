# Jan Sahayak: Government Welfare Scheme Assistant (GenAI + LLM)

A Generative AI assistant that helps citizens discover and understand Indian government welfare schemes.
Built as a project for the RTD Open Elective (GenAI and Large Language Models for a societal use case).

## Problem
Many eligible citizens never claim welfare benefits because scheme information is scattered across portals
and written in complex language.

## What it does
1. **Eligibility finder**: enter age, gender, occupation and annual family income; a rule-based engine lists matching schemes.
2. **Question answering (RAG)**: ask a free-text question; the system retrieves relevant scheme text and Flan-T5 answers using only that context.
3. **Plain-language explanations**: benefits, documents and how to apply, with the source scheme shown.
4. **Safe fallback**: if no relevant scheme is found (similarity < 0.30), the bot declines and points to the official portal.

## Architecture
![Architecture](docs/architecture.png)

Pipeline: scheme database -> eligibility filter / MiniLM embeddings -> FAISS retrieval -> grounded prompt -> Flan-T5 -> Gradio UI.

![Flowchart](docs/flowchart.png)

## Tech stack
Python, Hugging Face Transformers (`google/flan-t5-base`), Sentence-Transformers (`all-MiniLM-L6-v2`), FAISS, Gradio, Pandas, Matplotlib.

## Run it
**Google Colab (easiest):** open `Jan_Sahayak_Scheme_Assistant.ipynb` in Colab, choose *Runtime -> Run all*, and use the Gradio link.

**Locally:**
```bash
pip install -r requirements.txt
jupyter notebook Jan_Sahayak_Scheme_Assistant.ipynb
```

## Evaluation
The notebook (Step 8) reports eligibility accuracy, top-2 retrieval accuracy and response time.
Add your results here after running it:

| Metric | Result |
|---|---|
| Eligibility engine (7 test profiles) | _fill in_ |
| Retrieval top-2 accuracy (12 queries) | _fill in_ |
| Avg response time | _fill in_ |

## Limitations
- Demonstration database of 16 central schemes; state schemes not covered.
- Scheme rules change; verify on [myscheme.gov.in](https://www.myscheme.gov.in) before applying.
- English only; small Flan-T5 model gives short answers.

## Future work
Regional languages and voice, WhatsApp deployment, automatic scheme updates from official portals, document OCR.

## Disclaimer
This is an academic project. It provides guidance only and is not an official eligibility decision.

## License
MIT
