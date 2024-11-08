
# NAO Robot LLM API

## Project Overview

This project demonstrates the deployment of a large language model (LLM) using **Llama-2-13B** on a Flask-based API. The setup enables users to interact with the LLM through a web interface powered by Flask and Flask-Ngrok, allowing efficient hosting and testing.

## Features

1. **Model Deployment**: Llama-2-13B-chat is downloaded from Hugging Face and used for text generation.
2. **Flask API**: A lightweight Flask application provides endpoints for users to send queries and receive model responses.
3. **Ngrok Integration**: Flask-Ngrok or PyNgrok is used to expose the Flask app to the internet, making it accessible via a public URL.

## Prerequisites

- Python 3.x
- Google Colab with GPU runtime enabled
- Libraries: `llama-cpp-python`, `huggingface_hub`, `flask`, `flask-ngrok`, `pyngrok`

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-repo/NAO-Robot-LLM.git
cd NAO-Robot-LLM
```

### 2. Install Dependencies

On your Colab environment or local machine, install the required Python packages:

```bash
!pip install llama-cpp-python==0.1.78 numpy==1.23.4 huggingface_hub flask flask-ngrok pyngrok==4.1.1
```

### 3. Configure Ngrok

Set up your Ngrok authtoken to allow public exposure of your local Flask app:

```bash
!ngrok authtoken 'YOUR_NGROK_AUTH_TOKEN'
```

### 4. Running the Application

Run the Flask app directly from the Colab notebook:

```python
from flask import Flask, request, jsonify
from flask_ngrok import run_with_ngrok

app = Flask(__name__)
run_with_ngrok(app)  # Starts the ngrok tunnel

@app.route("/")
def home():
    return "<h1>Welcome to the NAO Robot LLM API</h1>"

@app.route('/query', methods=['POST'])
def query():
    # Process input and return model response
    pass

app.run()
```

## Key Highlights

- **Model**: Llama-2-13B-chat GGML version with GPU optimization.
- **API Endpoint**: Users can send queries via the `/query` endpoint and receive text-based responses from the LLM.

## Performance

- **GPU Acceleration**: Leverages Google Colabâ€™s GPU for fast model inference.
- **Efficiency**: Uses `llama-cpp-python` with optimized parameters (`n_gpu_layers=32`) for seamless execution.

## Additional Notes

This project runs on **Google Colab**, utilizing **Google's GPU** for efficient computation. Ensure you enable the GPU runtime in Colab by navigating to:

`Runtime > Change runtime type > Hardware accelerator > GPU`

This setup significantly enhances the model's performance, making it suitable for handling complex queries.