
# Multi-LLM-Evaluation-Framework

A professional and streamlined framework for evaluating the performance of multiple large language models (LLMs) on a single generated question. This tool facilitates fair comparison and ranking of model responses using another LLM as a judge.

---

## 🔍 Purpose

This project helps benchmark how different LLMs respond to a **challenging and nuanced prompt**. It:

* Automatically generates a single complex question using a host LLM.
  
* Sends that question to various LLMs (contestants).
  
* Collects their responses.
  
* Sends all answers to a judge LLM for ranking.
  
* Outputs results in a clean, ranked format.

---

## 🧠 Models Used

* **Question Generator:** Groq (LLaMA 3.3 70B Versatile)
  
* **Contestant LLMs:**

  * LLaMA 3.3 70B Versatile
    
  * Gemini 2.0 Flash
    
  * DeepSeek R1 Distill LLaMA 70B
    
  * Qwen QWQ 32B
    
  * LLaMA 3 8B
    
  * Mistral SABA 24B
    
* **Judge:** GPT-4o (via OpenAI)

---

## ⚙️ How It Works

1. A **challenging question** is created by LLaMA 3.3 70B.
   
2. The question is sent to each LLM, and their responses are collected.
   
3. The responses are **combined** and sent to GPT-4o for evaluation.
   
5. GPT-4o returns a **JSON ranking** of the competitors.

---
# Multi-LLM Evaluation Workflow:
                 ┌─────────────────────┐
                 │    Host LLM (70B)   │
                 │ e.g., LLaMA3-70B    │
                 └────────┬────────────┘
                          │
                          ▼
        ┌────────────────────────────────────┐
        │ Generates a complex, nuanced       │
        │ question to challenge other LLMs   │
        └────────────────┬───────────────────┘
                          │
                          ▼
          ┌────────────────────────────────┐
          │  Question sent to Competitors  │
          └────────────────────────────────┘
                          │
         ┌────────────────┼────────────────────────────┬────────────┬────────────┐
         ▼                ▼                            ▼            ▼            ▼
┌─────────────┐  ┌────────────────┐          ┌────────────────┐  ┌──────────┐ ┌──────────┐
│ LLaMA3-8B   │  │ Qwen-32B       │          │ Gemini-2 Flash │  │ Mistral  │ │ Mixtral  │
│ (Groq API)  │  │ (Groq API)     │          │ (Google API)   │  │ (Groq)   │ │ (Groq)   │
└────┬────────┘  └────┬───────────┘          └────┬────────────┘  └────┬─────┘ └────┬─────┘
     │               │                            │                   │            │
     ▼               ▼                            ▼                   ▼            ▼
Answers captured and stored ➝ Combined into a unified format
                          │
                          ▼
         ┌────────────────────────────────────┐
         │   Answers sent to Judge LLM (GPT)  │
         │         e.g., GPT-4o               │
         └────────────────┬───────────────────┘
                          │
                          ▼
       ┌───────────────────────────────────────────┐
       │ Judge evaluates responses based on:       │
       │ - Depth                                   │
       │ - Clarity                                 │
       │ - Relevance & Nuance                      │
       └────────────────┬──────────────────────────┘
                          │
                          ▼
             ┌────────────────────────────┐
             │   Final Ranking Returned   │
             │   in JSON Format           │
             └────────────────────────────┘
---

## 🛠️ Tech Stack

* Python (Colab Notebook)
  
* Groq SDK
  
* OpenAI SDK
  
* Google Generative AI SDK
  
* Markdown rendering (IPython display)

---

## 🧪 Example Output

```json
{"results": ["2", "5", "1", "4", "6", "3"]}
```

This indicates the ranking of each model by answer quality.

---

## ✅ Ideal Use Cases

* Evaluating and comparing new LLMs
  
* Research experiments for LLM capabilities
  
* Automated QA benchmarking pipelines

---

## 📌 Notes

* All responses and rankings are **subjective** to the judge model.
  
* This framework is designed to be **extensible** – more LLMs can be added easily.

---

## 🧑‍💻 Author

**Faiaz Ahmed**

---

## 📜 License

MIT License
