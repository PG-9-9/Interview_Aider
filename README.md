# Interview Aider

## Overview
**Interview Aider** is a **FastAPI-based** web application designed to process PDF documents, extract relevant information, and generate a structured Q&A output. It utilizes **LangChain**, **OpenAI**, and **FAISS** for intelligent document analysis and automatic question-answer generation. This application is particularly useful for **interview preparation, document summarization, and knowledge extraction** from large textual datasets.

## Features
- **Upload PDF Documents**: Allows users to upload PDF files for text extraction and processing.
- **AI-Powered Q&A Generation**: Uses a **LangChain-based pipeline** for generating context-aware Q&A pairs.
- **Storage & Retrieval**: Extracted data is stored efficiently, and results are saved in CSV format for easy accessibility.
- **FastAPI Backend**: Provides structured and well-documented API endpoints.
- **Jinja2-Based UI**: Uses Jinja2 templates for rendering a simple web-based interface.
- **Dockerized Deployment**: Can be deployed as a containerized application.

## Technologies Used
- **Programming Language**: Python 3.8+
- **Web Framework**: FastAPI
- **Machine Learning & NLP**: LangChain, OpenAI API, FAISS
- **Document Processing**: PyPDF2, pypdf
- **Data Handling**: Pandas
- **Asynchronous File Handling**: aiofiles
- **Templating Engine**: Jinja2
- **Containerization**: Docker

## Repository Link
[GitHub Repository](https://github.com/PG-9-9/Interview_Aider.git)

## Project Structure
```
Interview_Aider/
│── static/               # Static files (CSS, JS, PDFs, Output files)
│── templates/            # HTML templates (Jinja2)
│── src/
│   ├── helper.py         # LLM processing pipeline
│── app.py                # FastAPI application
│── requirements.txt      # Python dependencies
│── Dockerfile            # Docker configuration
│── setup.py              # Package setup file
```

## Installation Guide
### Prerequisites
Ensure you have the following installed:
- **Python 3.8+**
- **pip**
- **Docker (optional for deployment in containers)**

### Steps
1. **Clone the repository**
   ```sh
   git clone https://github.com/PG-9-9/Interview_Aider.git
   cd Interview_Aider
   ```
2. **Create a virtual environment**
   ```sh
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```
3. **Install dependencies**
   ```sh
   pip install -r requirements.txt
   ```
4. **Run the application**
   ```sh
   python app.py
   ```
   The application will be available at: `http://localhost:8080`

## API Endpoints
| Method | Endpoint        | Description |
|--------|----------------|-------------|
| **GET**  | `/`             | Renders the home page |
| **POST** | `/upload`       | Uploads a PDF file |
| **POST** | `/analyze`      | Processes the PDF and generates a Q&A CSV file |

### Upload PDF
**Endpoint:** `/upload`
- **Method:** `POST`
- **Params:** `pdf_file (File)`, `filename (str)`
- **Response:** `{ "msg": "success", "pdf_filename": "path_to_pdf" }`

### Analyze PDF
**Endpoint:** `/analyze`
- **Method:** `POST`
- **Params:** `pdf_filename (str)`
- **Response:** `{ "output_file": "static/output/QA.csv" }`

## Technical Details
### **LLM-Based Processing**
- Uses **LangChain** to interact with **OpenAI’s API**, forming a pipeline that extracts key information and generates question-answer pairs.
- **Vector Embeddings with FAISS**: The extracted text is vectorized and indexed using FAISS for efficient retrieval-based Q&A generation.

### **File Handling and Processing**
- The FastAPI app handles **PDF uploads asynchronously** using `aiofiles`, ensuring efficient file storage.
- Extracted text is saved in **static/docs/** and processed for Q&A generation.

### **Output Generation**
- Extracted **Q&A pairs** are stored in CSV format (`static/output/QA.csv`) for easy accessibility and analysis.

## Docker Deployment
To deploy using Docker:
1. **Build the Docker image**
   ```sh
   docker build -t interviewaider .
   ```
2. **Run the container**
   ```sh
   docker run -p 8080:8080 interviewaider
   ```
3. **Access the application**
   Visit `http://localhost:8080`

## Contributing
Contributions are welcome! Please follow these steps:
1. **Fork** the repository.
2. **Create a feature branch**.
3. **Make changes and commit**.
4. **Submit a Pull Request**.

## License
This project is licensed under the MIT License. Feel free to contribute or modify as needed!

---
Developed by **PG-9-9** | Contact: vishaals0507@gmail.com
