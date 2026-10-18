# 💬 Intelligent Chat Analysis

> A Streamlit web app that detects **intent**, recognises **emotion**, classifies **message type** and generates a **conversation summary** from customer-support chats — using a transparent, keyword-based NLP approach.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Streamlit](https://img.shields.io/badge/Built%20with-Streamlit-FF4B4B)
![License](https://img.shields.io/badge/License-MIT-green)

Built as an **ITA (Text Analytics / NLP) mini project** at K. J. Somaiya School of Engineering, Mumbai.

---

## ✨ Features

| Feature | What it does |
|---|---|
| **Three input modes** | Paste a chat, upload a `.txt` / `.csv` file (pick the message column), or run a built-in sample |
| **Text pre-processing** | Cleans line breaks and extra whitespace; skips empty messages |
| **Intent detection** | 9 intents: Refund Request, Order Tracking, Technical Support, Billing / Payment, Cancellation, Product Inquiry, Complaint, Appreciation, General Inquiry (else *Other / Unclear*) |
| **Emotion recognition** | Frustration, Satisfaction, Happiness, Sadness, Confusion (else *Neutral*) |
| **Message classification** | Complaint, Request, Inquiry, Feedback, Appreciation (else *General*) |
| **Conversation summary** | Auto-generated paragraph with dominant intent, emotion and category |
| **Dashboard** | Metrics, interactive Plotly bar chart (intents) and donut chart (emotions) |
| **Message-by-message table** | Every message with its labels and word count |
| **CSV export** | Download results as `chat_analysis_results.csv` |

## 📸 Screenshots

| Home | Metrics & summary |
|---|---|
| ![Home](screenshots/01-home.png) | ![Metrics](screenshots/02-metrics-summary.png) |

| Charts | Results table |
|---|---|
| ![Charts](screenshots/03-charts.png) | ![Table](screenshots/04-results-table.png) |

## 🧠 How it works

```
Input (paste / TXT / CSV / sample)
        │
   clean_text()  →  lower-case + whitespace normalisation
        │
 keyword scoring against lexicons  (intent · emotion · category)
        │
 label with highest score wins  (default label if score = 0)
        │
 DataFrame  →  summary · charts · table · CSV export
```

For each message, the score of a label is the number of its keywords/phrases found in the text. The highest-scoring label is chosen; if nothing matches, a default label is used.

**NLP concepts used:** text cleaning, case folding, regular expressions, lexicon-based classification, phrase matching, frequency analysis, template-based summarisation, data visualisation.

## 🚀 Getting started

```bash
# 1. Clone
git clone https://github.com/samruddhidev/intelligent-chat-analysis.git
cd intelligent-chat-analysis

# 2. (Optional) virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run
streamlit run app.py
```

The app opens at `http://localhost:8501`.

## 📂 Project structure

```
intelligent-chat-analysis/
├── app.py                 # Streamlit app (UI + NLP logic)
├── requirements.txt
├── sample_data/
│   └── sample_chat.csv    # Try this in the Upload tab (choose the "message" column)
├── screenshots/
├── LICENSE
└── README.md
```

## 🧪 Try it

Paste this into the **Paste chat** tab:

```
Customer: Where is my order? Delivery is late and it hasn't arrived.
Customer: This is unacceptable, I am very frustrated!
Agent: I'm sorry for the delay. Could you share your order details?
Customer: Thanks, I appreciate the quick help. Great service!
```

## ⚠️ Limitations

This is a **prototype**. Keyword matching cannot handle:

- sarcasm, negation (e.g. *"not happy"*) or deeper context
- slang, typos, emojis or non-English text
- more than one intent/emotion per message (only the top label is kept)
- speaker roles (agent and customer messages are treated alike)
- substring false positives (e.g. a polite *"sorry to hear that"* may be tagged Sadness)

It has not been evaluated on a labelled dataset and should not be used to make decisions about people.

## 🔮 Future scope

- Train ML / transformer models (Naive Bayes, SVM, BERT) for intent and emotion
- Negation handling, whole-word matching, lemmatisation, spelling correction
- Separate customer vs agent analysis and sentiment trend over time
- Abstractive summaries with sequence-to-sequence / LLM models
- Hindi / Marathi / code-mixed and emoji support
- Live integration with helpdesk or chat APIs
- Accuracy, precision, recall, F1 and confusion matrix on labelled data

## 👩‍💻 Authors

- **Samruddhi Jain** — [@samruddhidev](https://github.com/samruddhidev)
- **Insiya Lokhandwala**

## 📄 License

Released under the [MIT License](LICENSE).
