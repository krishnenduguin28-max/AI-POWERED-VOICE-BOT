# AI-Powered Voice Bot for Customer Support Automation

## Project Overview

This project implements an **AI-powered voice bot system** capable of
handling basic customer support queries using speech interaction. The
system accepts voice input, converts speech into text, identifies the
user's intent, generates an appropriate response, and returns the
response as synthesized speech.

The objective of the system is to demonstrate the development of a
complete **end-to-end machine learning pipeline** integrating speech
processing, natural language understanding, response generation, and API
deployment.

The system is designed with a **modular architecture**, allowing
individual components such as Automatic Speech Recognition (ASR), Intent
Classification, Response Generation, and Text-to-Speech (TTS) to operate
independently while being integrated through a FastAPI backend.


## Key Features

-   Speech-to-text conversion using **Whisper ASR**
-   Intent classification for **10 customer support intents**
-   Response generation based on predicted intent
-   Text-to-speech synthesis using **Google TTS**
-   REST API deployment using **FastAPI**
-   End-to-end **audio-to-audio voice interaction**
-   Evaluation using **Word Error Rate (WER)** and classification metrics
-   System latency measurement



## System Architecture

!(Architecture_Diagram.png) 


## Technologies Used

| Component | Technology |
|--------|--------|
| Programming Language | Python |
| Speech Recognition | Whisper |
| NLP Model | TF-IDF + Logistic Regression |
| Text-to-Speech | gTTS |
| API Framework | FastAPI |
| Machine Learning Libraries | Scikit-learn |
| Visualization | Matplotlib, Seaborn |
| Evaluation | JiWER |


## Setup Instructions

### 1. Install Python Dependencies

pip install -r requirements.txt


### 2. Install FFmpeg

Download FFmpeg from:

https://www.gyan.dev/ffmpeg/builds/

Download:

ffmpeg-release-essentials.zip

Steps:

1.  Extract the zip file
2.  Open the `bin` folder
3.  Copy the folder path
4.  Add it to **Windows Environment Variables -> PATH**

Verify installation:

ffmpeg -version


### 3. Train the Intent Classification Model

python nlp/train_intent_model.py

This will generate:

models/intent_model.pkl

models/vectorizer.pkl


### 4. Test Intent Prediction

python nlp/intent_predictor.py

Example:

Input:

where is my order

Output:

Predicted Intent: order_status

Confidence: 0.41


### 5. Test Speech Recognition

python asr/whisper_asr.py

Expected output:

Transcribed Text: Where is my order?

### 6. Test Response Generation

python -m tests.test_response

### 7. Test Text-to-Speech

python tts/tts_engine.py

This will generate:

response.mp3

### 8. Run the FastAPI Server

uvicorn app.main:app --reload

Server URL:

http://127.0.0.1:8000

API documentation:

http://127.0.0.1:8000/docs


## API Endpoints

  Endpoint

  /transcribe

  /predict-intent

  /generate-response

  /synthesize

  /voicebot


## Model Evaluation

### Intent Classification

Accuracy: **0.875**

Metrics reported:

-   Precision
-   Recall
-   F1 Score
-   Confusion Matrix

### Speech Recognition

Ground Truth: where is my order\
Predicted: Where is my order?

WER: **0.25**

### System Latency

Total Latency: **1.59 seconds**

This satisfies the requirement of **under 3-5 seconds**.


## Example Voicebot Interaction

User:

Where is my order?

System:

Intent: order_status

Response: Your order is currently being processed and will be delivered
soon.

Audio response is generated and returned.

## Future Improvements

-   Using transformer-based models such as **BERT**
-   Supporting **real-time microphone input**
-   Deploying the system on **cloud infrastructure**
-   Adding **multi-language support**
-   Implementing **context-aware conversation memory**

## Conclusion

This project demonstrates a complete **AI-powered voice bot system**
integrating speech recognition, natural language processing, response
generation, and speech synthesis. The modular architecture and REST API
deployment enable scalable and maintainable voice-based customer support
automation.
