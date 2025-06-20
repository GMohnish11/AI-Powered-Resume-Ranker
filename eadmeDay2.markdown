# AI-Powered Resume Ranker

## Project Description
This project ranks resumes based on their relevance to a job description using Natural Language Processing (NLP) techniques. It extracts text from resumes, converts them into embeddings, and computes similarity scores against a job description using cosine similarity.

## Tech Stack
- **Python**: Core programming language
- **Scikit-learn**: For vectorization and cosine similarity
- **spaCy**: For NLP text processing
- **Streamlit**: Optional UI component
- **JSON**: For storing sample resumes and job descriptions
- **Markdown**: For documentation

## Directory Structure
```
resume-ranker/
│
├── data/
│   ├── resumes/            # Sample resumes in JSON format
│   └── job_descriptions/   # Sample job descriptions in JSON format
│
├── core/
│   ├── extractor.py        # Extracts text/content from resumes
│   ├── vectorizer.py       # Converts resumes and JDs into embeddings
│   └── ranker.py           # Computes similarity scores
│
├── ui/
│   └── app.py              # Streamlit interface (optional)
│
├── tests/
│   └── test_ranker.py      # Unit tests for core logic
│
├── README.md               # Project documentation
├── requirements.txt        # Python dependencies
└── run.py                  # Main pipeline script
```

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd resume-ranker
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Download spaCy model:
   ```bash
   python -m spacy download en_core_web_sm
   ```
4. Run the pipeline:
   ```bash
   python run.py
   ```
5. (Optional) Launch Streamlit UI:
   ```bash
   streamlit run ui/app.py
   ```

## Adding New Resumes or Job Descriptions
- **Resumes**: Add new JSON files to `data/resumes/`. Format:
  ```json
  {
    "id": "resume_1",
    "content": "Full Name\nSoftware Engineer\nExperience: Python, Java..."
  }
  ```
- **Job Descriptions**: Add new JSON files to `data/job_descriptions/`. Format:
  ```json
  {
    "id": "jd_1",
    "content": "Job Title: Data Scientist\nRequirements: Python, Machine Learning..."
  }
  ```

## How Ranking Works
1. **Text Extraction**: `extractor.py` reads JSON files and extracts the `content` field.
2. **Vectorization**: `vectorizer.py` uses spaCy for tokenization and Scikit-learn's TF-IDF to create embeddings for resumes and job descriptions.
3. **Ranking**: `ranker.py` computes cosine similarity between the job description embedding and each resume embedding. Higher scores indicate better matches.
4. **Pipeline**: `run.py` orchestrates the process and outputs ranked resumes with scores.

## Sample Output
Running `python run.py` with sample data might produce:
```
Ranking for Job Description: jd_1
1. resume_1: 0.92
2. resume_2: 0.85
3. resume_3: 0.78
```

## Teammate Task Candidates
- **Data Expansion**: Add more sample resumes and job descriptions to `data/`.
- **UI Development**: Implement a Streamlit interface in `ui/app.py` for uploading resumes/JDs and displaying rankings.
- **Documentation**: Enhance `README.md` with diagrams or detailed instructions.

## Running Tests
Run unit tests to verify core functionality:
```bash
python -m unittest tests/test_ranker.py
```

## Notes
- Ensure JSON files are properly formatted to avoid parsing errors.
- The Streamlit UI is optional and can be developed independently.
- Extend `tests/test_ranker.py` to cover additional edge cases.