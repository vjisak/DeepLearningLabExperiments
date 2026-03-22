Deep Learning Lab — Experiments 5 to 8

A collection of four deep learning experiments covering MIMO models, Bidirectional RNNs, Transfer Learning, and LSTM Text Generation.
Built and run on Google Colab | Uploaded to GitHub


Table of Contents

Experiment 5 — Student Performance Prediction
Experiment 6 — Next Word Prediction using Stacked BiLSTM
Experiment 7 — Sentiment Analysis using Hugging Face
Experiment 8 — Harry Potter Text Generation using LSTM
Tech Stack
How to Run


Experiment 5 — Student Performance Prediction
Topic: Exploring Multi-Input Multi-Output Models with Hyperparameter Tuning
Problem Statement
Traditional student performance prediction systems struggle to accurately forecast overall academic performance when handling multiple influencing factors simultaneously. This experiment builds a MIMO neural network optimized automatically using the Optuna hyperparameter tuning framework.
Input Features
FeatureDescriptionSleep HoursDaily hours of sleep (4–10)Previous GPAAcademic GPA from prior term (2.0–4.0)ExtracurricularParticipation in activities (0 = No, 1 = Yes)Attendance %Class attendance percentage (50–100%)
Output

Overall Performance Score (0–100)

Model

Sequential Neural Network (Dense layers)
Optuna searches: n_layers, n_units, learning_rate, batch_size
20 trials → best params → 50 epoch final training

Results
MetricValueTest MSE Loss18.47Test MAE3.21Sample Prediction74.58 / 100

Sample input: Sleep=7hrs, GPA=3.2, Extracurricular=Yes, Attendance=85%


Experiment 6 — Next Word Prediction using Stacked BiLSTM
Topic: Language Modeling using Stacked Bidirectional RNNs
Problem Statement
Single-layer RNN models fail to capture long-term dependencies in text. This experiment builds a Stacked Bidirectional LSTM for next-word prediction trained on a custom Movie & Book Quotes dataset.
Dataset
Custom corpus of 40 famous movie and book quotes covering themes of life, courage, dreams, and perseverance.
Model Architecture
Embedding (64 dims)
      ↓
Bidirectional LSTM (128 units, return_sequences=True)
      ↓
Dropout (0.3)
      ↓
Bidirectional LSTM (64 units)
      ↓
Dropout (0.3)
      ↓
Dense Softmax Output
Sample Predictions
Input PhrasePredicted Next Wordto be or notbethe best time toplantlife is whathappensthe mind iseverythingyou only liveonce
Results

Training: 200 epochs, Adam optimizer
Loss: categorical_crossentropy
Final Test Accuracy: ~86%


Experiment 7 — Sentiment Analysis using Hugging Face
Topic: Transfer Learning Models for Classification — Exploring Hugging Face API
Problem Statement
Traditional classifiers struggle with nuanced sentiment in movie reviews. This experiment fine-tunes DistilBERT (a lightweight transformer) from Hugging Face on a custom movie review dataset to classify sentiment as Positive or Negative.
Dataset
50 custom movie review sentences — 25 Positive, 25 Negative.
Model

DistilBERT (distilbert-base-uncased) — pre-trained transformer
Fine-tuned for binary sequence classification
4 training epochs, batch size 8

Sample Predictions
InputSentimentConfidenceThis was an absolutely wonderful experience😊 POSITIVE97.4%Terrible movie I hated every minute😞 NEGATIVE96.1%A masterpiece of modern cinema😊 POSITIVE95.8%Boring and pointless I want my money back😞 NEGATIVE94.3%
Key Fix

Newer versions of Hugging Face renamed evaluation_strategy → eval_strategy in TrainingArguments.


Experiment 8 — Harry Potter Text Generation using LSTM
Topic: Text Generation using LSTM with Gradio Web Interface
Problem Statement
To build a character-level text generation model that learns and mimics the style of Harry Potter text using LSTM neural networks, deployed via an interactive Gradio web interface.
Dataset
Custom Harry Potter style corpus (~5000 characters) covering characters, spells, locations, and storylines from the series.
Model Architecture
LSTM (256 units, return_sequences=True)
      ↓
Dropout (0.3)
      ↓
LSTM (128 units)
      ↓
Dropout (0.3)
      ↓
Dense Softmax Output (vocab_size)
Parameters
ParameterValueSequence Length40 charactersStep Size3Batch Size128Epochs60Temperature0.6 (default)
Sample Output
Seed:      "harry potter was"
Generated: "harry potter was a young wizard who lived in the
            wizarding world and knew that dumbledore had always
            told him the magic of love was the greatest spell..."
Gradio UI
Interactive web interface with:

Seed text input
Generation length slider (50–300)
Temperature slider (0.2–1.0) for creativity control


🛠 Tech Stack
LibraryPurposeTensorFlow / KerasNeural network building & trainingOptunaAutomated hyperparameter tuning (Exp 5)Hugging Face TransformersPre-trained transformer models (Exp 7)PyTorchBackend for Hugging Face models (Exp 7)GradioInteractive web UI (Exp 8)Scikit-learnPreprocessing, train/test splitNumPy / PandasData manipulationMatplotlibTraining plots and visualizationsGoogle ColabRuntime environment (free GPU)

▶ How to Run

Open Google Colab
Click File → New Notebook
Copy the code from the respective experiment's .ipynb file
Run each cell top to bottom
For Exp 7, make sure to use eval_strategy (not evaluation_strategy)
For Exp 8, the Gradio link will appear after the last cell runs


 Repository Structure
 deep-learning-lab-exp-5-to-8
 ┣  Exp5_Student_Performance_MIMO_Optuna.ipynb
 ┣  Exp6_NextWord_BiLSTM_MovieQuotes.ipynb
 ┣  Exp7_Sentiment_DistilBERT_HuggingFace.ipynb
 ┣  Exp8_TextGen_LSTM_HarryPotter.ipynb
 ┣  exp5_training_plot.png
 ┣  exp6_training_plot.png
 ┣  exp8_training_loss.png
 ┗  README.md


📌 Institution: Dr. N.G.P. Institute of Technology, Coimbatore
🔬 Subject: Deep Learning Lab
