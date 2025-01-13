# Dense Passage Retrieval Project for Stoic Notes

## Project Overview

This project implements an end-to-end Dense Passage Retrieval (DPR) system for retrieving relevant passages from a collection of stoic notes. DPR uses bi-encoder models from Hugging Face for encoding questions and passages, enabling efficient and accurate retrieval. The project is modular, with a focus on scalability, reusability, and ease of deployment.

---

## Features

- **Data Ingestion**: Load and preprocess raw text data.
- **Dense Encoding**: Use Hugging Face DPR models to encode passages and queries.
- **Efficient Retrieval**: Build a FAISS index for fast and accurate passage retrieval.
- **Flask API**: Query the system via a RESTful API.
- **Modular Design**: Easily extend or customize components for additional use cases.

---

## Project Structure

```
stoic_dpr_project/
│
├── data/
│   ├── raw/                 # Raw stoic notes text files
│   └── processed/           # Processed data for DPR
│
├── src/
│   ├── __init__.py
│   ├── data_ingestion.py    # Handles data loading
│   ├── data_transformer.py  # Processes raw text into embeddings
│   ├── model_trainer.py     # Sets up DPR model and training
│   ├── retriever.py         # Retrieves passages based on user queries
│   ├── app.py               # Flask application for deployment
│
├── tests/
│   ├── test_data_ingestion.py
│   ├── test_data_transformer.py
│   └── test_retriever.py
│
├── setup.py
├── requirements.txt
└── README.md
```

---

## Setup Instructions

### Prerequisites

- Python 3.8 or later
- Pip (Python package installer)
- Virtual environment (recommended)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/stoic_dpr_project.git
   cd stoic_dpr_project
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate # On Windows: venv\Scripts\activate
   ```

3. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Install the project as a package:
   ```bash
   python setup.py install
   ```

---

## Usage

### Data Preparation

1. Place your raw stoic notes in the `data/raw/` directory as `.txt` files.
2. The system will process these files during ingestion.

### Running the Application

Start the Flask API:

```bash
python src/app.py
```

The API will be available at `http://localhost:5000`.

### Querying the API

Send a POST request to the `/query` endpoint with your query text:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"query": "What is stoicism?"}' http://localhost:5000/query
```

### Expected Response

A JSON object with the top retrieved passages:

```json
["Passage 1 content...", "Passage 2 content..."]
```

---

## Testing

Run the tests to ensure everything works as expected:

```bash
pytest tests/
```

---

## Future Scope

- Integration with additional pre-trained models.
- Improved indexing strategies (e.g., hybrid search).
- Frontend interface for user interaction.
- Deploying the application using Docker or cloud platforms (AWS, GCP).

---

## License

This project is licensed under the MIT License. See `LICENSE` for more details.

---

## Acknowledgments

- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [FAISS: Facebook AI Similarity Search](https://faiss.ai/)
