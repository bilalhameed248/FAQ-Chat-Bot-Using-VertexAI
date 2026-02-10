# FAQ Chat Bot Using VertexAI

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.0%2B-green.svg)](https://flask.palletsprojects.com/)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-VertexAI-orange.svg)](https://cloud.google.com/vertex-ai)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> An intelligent FAQ chatbot powered by Google's TextEmbeddings-Gecko@001 model, utilizing advanced text embeddings and cosine similarity for accurate question-answering.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Evaluation](#evaluation)
- [Logging](#logging)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This project implements a sophisticated FAQ chatbot using Google Cloud's Vertex AI and the TextEmbeddings-Gecko@001 model. The system leverages state-of-the-art natural language processing techniques to understand user queries and provide accurate responses based on a pre-defined knowledge base.

The chatbot uses semantic similarity matching through text embeddings and cosine similarity calculations to find the most relevant answers to user questions, making it highly effective for FAQ systems, customer support, and information retrieval applications.

## ✨ Features

### Core Functionality
- **🤖 Intelligent Question Matching**: Uses Google's TextEmbeddings-Gecko@001 model to generate high-quality text embeddings
- **🎯 Semantic Search**: Employs cosine similarity to find the most relevant answers to user queries
- **🌐 Flask API**: RESTful API endpoints for easy integration with front-end applications
- **📊 Pre-computed Embeddings**: Stores question-answer pairs with pre-generated embeddings in CSV format for fast retrieval

### Advanced Features
- **📝 Comprehensive Logging**: Automatic logging of all user interactions stored in the static directory
- **🔍 Evaluation System**: Automated testing mechanism that generates question variations and measures chatbot accuracy
- **📈 Performance Metrics**: Ground truth comparison and accuracy scoring for continuous improvement
- **⚡ Fast Response Time**: Optimized similarity search for real-time user interactions

## 🏗️ Architecture

The system follows a three-tier architecture:

1. **Data Layer**: CSV file containing questions, answers, and pre-computed embeddings
2. **Application Layer**: Flask backend handling API requests and similarity computations
3. **Presentation Layer**: Front-end interface for user interactions

```
User Query → Flask API → Embedding Generation → Cosine Similarity → Best Match → Response
```

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.8 or higher
- pip (Python package manager)
- Google Cloud account with Vertex AI API enabled
- Google Cloud credentials configured

## 🚀 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/bilalhameed248/FAQ-Chat-Bot-Using-VertexAI.git
   cd FAQ-Chat-Bot-Using-VertexAI
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Google Cloud credentials**
   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/credentials.json"
   ```

5. **Prepare your data**
   - Place your FAQ data CSV file in the appropriate directory
   - Ensure it contains columns for questions, answers, and embeddings

## 💻 Usage

### Starting the Flask Application

```bash
python app.py
```

The server will start on `http://localhost:5000` by default.

### Making API Requests

**Example using cURL:**
```bash
curl -X POST http://localhost:5000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"question": "What are your business hours?"}'
```

**Example using Python:**
```python
import requests

response = requests.post(
    'http://localhost:5000/api/chat',
    json={'question': 'What are your business hours?'}
)
print(response.json())
```

## 📁 Project Structure

```
FAQ-Chat-Bot-Using-VertexAI/
├── app.py                      # Main Flask application
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
├── data/
│   └── faq_embeddings.csv     # FAQ data with embeddings
├── static/
│   └── logs/                  # User interaction logs
├── models/
│   └── embedding_model.py     # Embedding generation logic
├── utils/
│   ├── similarity.py          # Cosine similarity calculations
│   └── evaluation.py          # Evaluation and testing utilities
└── tests/
    └── test_chatbot.py        # Unit and integration tests
```

## 🔌 API Endpoints

### POST `/api/chat`
Submit a question to the chatbot.

**Request Body:**
```json
{
  "question": "Your question here"
}
```

**Response:**
```json
{
  "question": "Your question here",
  "answer": "The bot's response",
  "confidence": 0.95,
  "timestamp": "2024-01-01T12:00:00Z"
}
```

## 📊 Evaluation

The chatbot includes an automated evaluation system that:

1. **Generates Test Variations**: Creates multiple variations of original FAQ questions
2. **Tests Responses**: Runs these variations through the chatbot
3. **Compares Results**: Matches responses against ground truth answers
4. **Calculates Metrics**: Provides accuracy scores and performance metrics

**Running Evaluations:**
```bash
python utils/evaluation.py
```

## 📝 Logging

All user interactions are automatically logged to the `static/logs/` directory. Logs include:
- User questions
- Bot responses
- Timestamps
- Confidence scores
- Session information

⭐ If you find this project useful, please consider giving it a star on GitHub!
