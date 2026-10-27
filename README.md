# 🤖 Multilingual AI Customer Support System

> AI-native multilingual customer support system for e-commerce, built with intent classification, retrieval-augmented responses, semantic embeddings, structured outputs, and an evaluation framework supporting English and Arabic.

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
[![AI](https://img.shields.io/badge/AI-Native-green.svg)]()
[![NLP](https://img.shields.io/badge/NLP-Embeddings-orange.svg)]()
[![Status](https://img.shields.io/badge/Status-Prototype-brightgreen.svg)]()

---

## 🎯 Overview

This project is an AI-native customer support system designed to handle e-commerce queries in English and Arabic using a hybrid AI pipeline combining intent classification, semantic embeddings, and a lightweight retrieval-augmented generation (RAG) system.

The system simulates a customer support assistant that understands paraphrased queries, retrieves relevant FAQ information, provides bilingual responses, and produces structured outputs with confidence scoring and fallback handling for unknown inputs.

It combines:

- Intent classification (rule-based + semantic)
- Embedding-based similarity matching
- Retrieval-Augmented Generation (FAQ grounding)
- Structured JSON output validation
- Confidence scoring and uncertainty handling
- Evaluation framework with measurable accuracy

---

## 🧠 Problem It Solves

Customer support teams face:

- Repeated queries about refunds, delays, and returns
- Mixed English and Arabic messages
- Unstructured user inputs
- Slow manual response handling
- Inconsistent responses across support agents

This system addresses these challenges by automatically:

- Identifying customer intent
- Retrieving relevant policy context
- Producing structured bilingual responses
- Handling uncertainty with safe fallback responses

---

## ⚙️ Key Features

### 🧩 AI Capabilities

- Intent classification for refunds, delays, product issues, order status, policies, shipping, and unknown queries
- Semantic understanding using sentence embeddings
- FAQ retrieval using similarity search (RAG-style)
- Confidence scoring for predictions
- Fallback handling for unknown queries

### 🌍 Multilingual Output

- English responses
- Arabic responses in Modern Standard Arabic

### 🧠 Structured Output

Every response follows a structured schema:

- `intent`
- `response_en`
- `response_ar`
- `confidence`
- `faq_used` (optional)

---

## 📊 Evaluation System

- 12+ test cases covering normal and adversarial inputs
- Reported accuracy of approximately 91.6%
- Robustness testing on noisy inputs
- Unknown-intent detection validation

---

## 🏗️ Architecture

User Input → Classifier (Rules + Embeddings) → FAQ Retriever → RAG Context Injection → Response Generator → Pydantic Validator → Structured JSON Output

---

## 📁 Project Structure

- `app.py` — CLI interface
- `classifier.py` — Intent classification engine
- `embeddings.py` — Sentence Transformer embeddings
- `rag.py` — FAQ retrieval system
- `response.py` — English and Arabic response generation
- `validator.py` — Structured schema validation using Pydantic
- `eval.py` — Evaluation pipeline
- `config.py` — Intent definitions and FAQ configuration
- `data.py` — Sample training and FAQ data
- `tools.py` — Utility functions
- `utils.py` — Helper functions
- `policies.txt` — Business rules

---

## 🚀 How to Run

### 1. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the support system

```bash
python app.py
```

### 4. Run evaluation tests

```bash
python eval.py
```

---

## 💬 Example Outputs

### Example 1: Refund Request

**User:** `I want my money back`

```json
{
  "intent": "refund_request",
  "response_en": "Refund is available within 30 days if the product is unused.",
  "response_ar": "يمكنك استرجاع المبلغ خلال 30 يوم إذا لم يتم استخدام المنتج.",
  "confidence": 0.77,
  "faq_used": "Returns accepted within 30 days of purchase."
}
```

### Example 2: Delayed Order

**User:** `my order is late`

```json
{
  "intent": "delay_issue",
  "response_en": "Your order may be delayed. Please share your order ID.",
  "response_ar": "قد يكون طلبك متأخراً. يرجى مشاركة رقم الطلب.",
  "confidence": 0.66
}
```

### Example 3: Unknown Query

**User:** `asdfgh random text`

```json
{
  "intent": "unknown",
  "response_en": "I need more details to help you.",
  "response_ar": "أحتاج إلى مزيد من التفاصيل لمساعدتك.",
  "confidence": 0.18
}
```

---

## 📊 Evaluation Results

- **Test cases:** 12
- **Reported accuracy:** 91.6%
- **Robustness:** Tested with noisy and adversarial inputs
- **Unknown-intent detection:** Evaluated
- **Confidence scoring:** Used across supported intents

---

## 🧠 Why This Is AI Engineering

This project combines multiple components into an AI pipeline:

- Classifier, retriever, and response-generation workflow
- Embedding-based semantic retrieval
- RAG-style FAQ grounding
- Structured output enforcement using Pydantic
- Confidence-aware fallback handling
- Multilingual response generation in English and Arabic

---

## ⚠️ Limitations

- No external LLM API is used; responses follow a lightweight local design.
- The dataset is synthetic and may not represent real-world customer queries.
- The interface is CLI-based, with no frontend UI.
- No persistent conversation memory is implemented.

---

## 🔥 Future Improvements

- Fine-tuned transformer classifier
- Vector database integration using FAISS or Pinecone
- Real-time support analytics dashboard
- WhatsApp or web chat integration
- Human escalation workflow
- Production API deployment using FastAPI

---

## 🧪 Tools and Technologies

- Python
- Sentence Transformers
- Scikit-learn
- Embedding-based similarity search
- Custom RAG-style FAQ retrieval
- Pydantic validation
- CLI-based interaction
- Custom evaluation pipeline

---

## ⏱️ Development Breakdown

- Design: 1 hour
- AI pipeline: 2 hours
- Implementation: 1.5 hours
- Evaluation: 0.5 hour

---

## 📌 Key Takeaways

This project demonstrates practical AI engineering concepts:

- Semantic understanding using embeddings
- Retrieval-augmented responses
- Structured output validation
- Evaluation-driven development
- Multilingual customer support
- Confidence scoring and fallback handling

---

## 🔄 Design Tradeoffs

- **Hybrid intent classification:** Combined rules and embeddings instead of using a large LLM to keep the system lightweight and predictable.
- **No fine-tuning:** Used semantic retrieval and classification to reduce development complexity and time.
- **Lightweight RAG:** Implemented FAQ similarity retrieval without deploying an external vector database.
- **Reliability over creativity:** Prioritized structured outputs and predictable support responses.

---

## 🧪 Tooling Explanation

- **Sentence Transformers:** Generates semantic embeddings to capture meaning beyond keyword matching.
- **Scikit-learn:** Supports lightweight classification and evaluation utilities.
- **Custom retrieval layer:** Matches queries against FAQ content without an external vector database.
- **Pydantic:** Validates structured response data.
- **AI-assisted development:** ChatGPT supported architecture refinement, edge-case generation, debugging, and multilingual response formatting.

---

## ⚠️ Failure Analysis and Known Weaknesses

- Short or ambiguous inputs such as `ok`, `123`, and `help` may receive low-confidence or incorrect classifications.
- Arabic output uses Modern Standard Arabic and may not reflect regional dialects.
- Semantically vague queries may overlap across multiple intents.
- Conversations are processed independently without session memory.
- The synthetic FAQ dataset limits real-world coverage and diversity.

---

## 🚀 Expected Behavior

After running `python app.py`:

- The CLI starts an interactive support session.
- Users can enter natural-language queries.
- The system returns structured JSON responses in English and Arabic.

Running `python eval.py` executes the evaluation pipeline and reports the measured results.
