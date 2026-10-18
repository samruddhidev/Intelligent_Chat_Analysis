# 💬 Intelligent Chat Analysis

A Streamlit web app that analyses customer-support conversations and reports the **intent**, **emotion** and **message type** of every message, along with an auto-generated **conversation summary** and interactive charts.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Streamlit](https://img.shields.io/badge/Built%20with-Streamlit-FF4B4B)
![License](https://img.shields.io/badge/License-MIT-green)

## ✨ Features

| Feature | Description |
|---|---|
| **Flexible input** | Paste a chat, upload a `.txt` / `.csv` file (choose the message column), or run the built-in sample |
| **Intent detection** | Refund Request, Order Tracking, Technical Support, Billing / Payment, Cancellation, Product Inquiry, Complaint, Appreciation, General Inquiry (otherwise *Other / Unclear*) |
| **Emotion recognition** | Frustration, Satisfaction, Happiness, Sadness, Confusion (otherwise *Neutral*) |
| **Message classification** | Complaint, Request, Inquiry, Feedback, Appreciation (otherwise *General*) |
| **Conversation summary** | Auto-generated overview of the dominant intent, emotion and category |
| **Dashboard** | Key metrics, an interactive intent bar chart and an emotion donut chart |
| **Detailed table** | Every message with its labels and word count |
| **CSV export** | Download the full analysis as `chat_analysis_results.csv` |

## 🧠 How it works

```
Input (paste / TXT / CSV / sample)
        ↓
Text cleaning (whitespace normalisation, lower-casing)
        ↓
Keyword scoring against intent, emotion and category lexicons
        ↓
Highest-scoring label wins (default label if nothing matches)
        ↓
Summary · Charts · Results table · CSV export
```

Each label has a list of keywords and phrases. A message's score for a label is the number of those keywords found in its text, and the label with the highest score is selected.

## 🚀 Getting started

```bash
# Clone the repository
git clone https://github.com/samruddhidev/intelligent-chat-analysis.git
cd intelligent-chat-analysis

# (Optional) create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py
```

The app opens at `http://localhost:8501`.

## 🧪 Quick test

Paste this into the **Paste chat** tab and click **Analyze pasted chat**:

```
Customer: Where is my order? Delivery is late and it hasn't arrived.
Customer: This is unacceptable, I am very frustrated!
Agent: I'm sorry for the delay. Could you share your order details?
Customer: Thanks, I appreciate the quick help. Great service!
```

You can also upload `sample_data/sample_chat.csv` in the **Upload file** tab and select the `message` column.

## 📂 Project structure

```
intelligent-chat-analysis/
├── app.py                  # Streamlit UI and analysis logic
├── requirements.txt        # Python dependencies
├── sample_data/
│   └── sample_chat.csv     # Example file for the upload tab
├── LICENSE
└── README.md
```

## ⚠️ Limitations

This is a lightweight prototype built on keyword matching, so it cannot reliably handle:

- Sarcasm, negation (e.g. *"not happy"*) or deeper context
- Slang, typos, emojis or non-English text
- Multiple intents or emotions in one message (only the top label is kept)
- Speaker roles (agent and customer messages are treated alike)
- Substring false positives (e.g. a polite *"sorry to hear that"* may be tagged as Sadness)

It has not been evaluated on a labelled dataset and should not be used to make decisions about people.

## 🔮 Future scope

- Train ML / transformer models (Naive Bayes, SVM, BERT) for intent and emotion
- Negation handling, whole-word matching and lemmatisation
- Separate customer and agent analysis, with emotion trends over time
- Abstractive summaries using sequence-to-sequence or LLM models
- Hindi / Marathi / code-mixed text and emoji support
- Live integration with helpdesk or chat platforms
- Accuracy, precision, recall, F1 and confusion-matrix evaluation

## 👩‍💻 Author

**Samruddhi Jain** — [@samruddhidev](https://github.com/samruddhidev)

## 📄 License

Released under the [MIT License](LICENSE).
