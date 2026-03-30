<div align="center">

![Frontend Tutor Agent Banner](frontend-tutor-banner.jpg)

<br/>

# 🎨 Frontend Tutor Agent

### *An AI Agent to solve all your frontend queries*

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Google Gemini](https://img.shields.io/badge/Gemini_2.5_Flash-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://deepmind.google/technologies/gemini/)
[![Google ADK](https://img.shields.io/badge/Google_ADK-34A853?style=for-the-badge&logo=google&logoColor=white)](https://google.github.io/adk-docs/)
[![FAISS](https://img.shields.io/badge/FAISS-FF6B35?style=for-the-badge&logo=meta&logoColor=white)](https://github.com/facebookresearch/faiss)
[![Kaggle](https://img.shields.io/badge/Kaggle_Capstone-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://kaggle.com)

<br/>

 **🏆 Google × Kaggle 5-Day AI Agents Intensive — Capstone Project**

<br/>

</div>

---

## 🌟 The Problem

Learning frontend development is **overwhelming for beginners**. Even seemingly simple tasks like centering a `div` or building a responsive layout require juggling multiple HTML and CSS concepts simultaneously.

Beginners face:

- 🔁 **Inconsistent** explanations scattered across tutorials
- 🗓️ **Outdated** layout patterns that no longer reflect best practices
- 🤔 **Translation gaps** turning plain English questions into working code

The result? Frustration. Slow learning curves. Discouragement.

What beginners really need is a tutor that *thinks*, *checks its own work*, and delivers **clean, correct, minimal code** — every time.

---

## 💡 Why an Agent?

A static chatbot just generates text. **An agent reasons, retrieves, validates, and self-corrects.**

| Capability | What It Does |
|---|---|
| 🔍 **Tool-Calling** | Retrieves known-good HTML/CSS snippets from a curated corpus — no hallucination |
| ✅ **Validation** | Checks generated code for correct layout patterns before returning it |
| 🔄 **Orchestration** | Auto-retries on validation failure — no manual re-prompting |
| 🧠 **Memory** | Stores interaction history for better long-term UX |
| 🔎 **Transparency** | Debug traces expose the full reasoning chain |

This mirrors how a **real tutor** actually works: *reference materials → validate → refine → deliver.*

---

## 🏗️ Architecture
 
```mermaid
flowchart TD
    Q([🙋 User Question\n&quot;How do I center a div with CSS?&quot;])
    
    Q --> G
 
    subgraph G ["&nbsp;&nbsp;🗂️  1 · Grounding Layer&nbsp;&nbsp;"]
        G1[Curated Snippet Corpus]
        G2[SentenceTransformer Embeddings]
        G3[FAISS Vector Index]
        G1 --> G2 --> G3
    end
 
    G --> T
 
    subgraph T ["🔧  2 · Tools Layer"]
        T1["🔍 retrieve_snippets\nFetch relevant HTML/CSS examples"]
        T2["✅ heuristic_validate\nCheck flex / grid / absolute patterns"]
    end
 
    T --> A
 
    subgraph A ["🤖  3 · Agent Layer"]
        A1["Gemini 2.5 Flash Lite\n+ Google ADK LlmAgent"]
        A2[Strict output format\nHTML block + CSS block only]
        A1 --- A2
    end
 
    A --> O
 
    subgraph O ["🔄  4 · Orchestration Layer"]
        O1[Run Agent]
        O2[Read Debug Traces]
        O3{Validator\nPassed?}
        O1 --> O2 --> O3
        O3 -- ❌ No --> O1
    end
 
    O3 -- ✅ Yes --> U
 
    subgraph U ["✨  5 · UX Layer"]
        U1[Session Memory]
        U2[Inline HTML/CSS Preview]
    end
 
    U --> R([🎉 Clean Code\n+ Visual Preview Delivered])
 
    style Q fill:#1e3a5f,color:#a8d8ff,stroke:#4a9eff
    style R fill:#1a3d2b,color:#a8ffcc,stroke:#3ddc84
    style G fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style T fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style A fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style O fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
    style U fill:#1a1a2e,color:#e0e0ff,stroke:#4a4aff
```

---

## 🚀 Demo Flow

Here's what happens when you ask **"How do I center a child div inside a parent using CSS?"**

```
1. 🔍  Agent retrieves 2–3 grounded snippets from the corpus

2. ✍️  Gemini generates minimal HTML/CSS using modern layout (flex / absolute)

3. ✅  heuristic_validate() checks the output:
       └─ Valid centering pattern found?
           ├─ YES → Return to user ✅
           └─ NO  → Retry automatically 🔄

4. 👁️  Inline HTML preview renders the final layout visually

5. 💬  User receives:
       ├─ Clean HTML block (with comments)
       ├─ Clean CSS block (with comments)
       └─ A working visual preview — no prose fluff
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| **LLM** | Gemini 2.5 Flash Lite |
| **Agent Framework** | Google ADK (`LlmAgent`, `FunctionTool`, `InMemoryRunner`) |
| **Embeddings** | SentenceTransformer (lightweight) |
| **Vector Search** | FAISS `IndexFlatIP` |
| **Validation** | Custom heuristic pattern checker |
| **Notebook** | Jupyter / Kaggle Notebook |
| **Preview** | Inline HTML rendering |

---

## 📁 Project Structure

```
frontend-tutor-agent/
│
├── 📓 frontend-tutor-code-assistant.ipynb   # Main Kaggle notebook
├── 🖼️  frontend-tutor-banner.jpg            # Project banner
└── 📄 README.md                             # You are here
```

---

## 🔬 Google × Kaggle AI Agents Intensive — Concepts Applied

This project directly applies concepts from all 5 days of the intensive:

- **Day 1** — Prompting & Structured Output (strict HTML/CSS-only format)
- **Day 2** — Embeddings & Vector Search (FAISS + SentenceTransformer grounding)
- **Day 3** — Agents & Tool Use (ADK `FunctionTool`, retrieval + validation tools)
- **Day 4** — Domain-Specific Agents (education-focused tutor persona)
- **Day 5** — Agent Orchestration (regenerate-on-fail retry loop, debug traces)

---

## 🔮 Future Enhancements

<details>
<summary><strong>Click to expand the roadmap</strong></summary>

<br/>

| Feature | Description |
|---|---|
| 🎭 **Visual DOM Validator** | Use Playwright/headless browser for pixel-accurate layout verification |
| 📦 **Larger Snippet Corpus** | Animations, navbars, cards, tabs, dark/light theming |
| 🧠 **User Preference Learning** | Remember if a user prefers `grid` over `flex`, `rem` over `px`, etc. |
| 📖 **Multi-Step Tutorials** | Step-by-step walkthroughs explaining *why* the code works |
| 🚀 **CodeSandbox Export** | One-click live editing in browser |
| 🌐 **Web App Deployment** | Full UI-powered frontend learning assistant |

</details>

---

## 📓 Notebook

Open the capstone notebook directly:

[![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](frontend-tutor-code-assistant.ipynb)

---

<div align="center">

<br/>

Built with ❤️ for the **Google × Kaggle 5-Day AI Agents Intensive**

*Capstone Project — Agents Intensive*

<br/>

*If this project helped you, consider leaving a ⭐ on the repo!*

</div>
