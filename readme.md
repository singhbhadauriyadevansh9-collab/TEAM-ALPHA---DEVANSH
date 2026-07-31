# TEAM-ALPHA — Research Paper Briefing Agent

An AI-powered application that helps students and researchers quickly understand research papers. It reads a PDF, extracts key claims, methods, results, and limitations, verifies each point with citations back to the original paper, and generates summaries, flashcards, and presentation-ready notes for faster, more trustworthy learning.

##  Features

- **PDF ingestion** — upload any research paper as a PDF and have it parsed automatically.
- **Structured extraction** — pulls out claims, methodology, results, and limitations instead of a generic summary.
- **Grounded citations** — every extracted point is verified and linked back to the exact location in the source paper, reducing hallucination risk.
- **Auto-generated study aids** — condensed summaries, flashcards, and presentation-ready notes for quick review.
- **Retrieval-augmented pipeline** — uses embeddings + a vector store so answers stay grounded in the actual paper content rather than the model's memory.

##  Tech Stack

| Layer | Technology |
|---|---|
| Backend API | [FastAPI](https://fastapi.tiangolo.com/) + [Uvicorn](https://www.uvicorn.org/) |
| PDF Parsing | [PyMuPDF](https://pymupdf.readthedocs.io/) |
| Embeddings | [sentence-transformers](https://www.sbert.net/) (PyTorch backend) |
| Vector Store | [ChromaDB](https://www.trychroma.com/) |
| LLM | [Google Gemini](https://ai.google.dev/) (`google-genai`) |
| File Uploads | `python-multipart` |
| Config | `python-dotenv` |

##  Project Structure

```
TEAM-ALPHA---DEVANSH/
├── backend/          # FastAPI service: PDF parsing, embeddings, retrieval, Gemini calls
├── frontend/         # Client application (UI for uploading papers and viewing briefs)
├── app.py            # Application entry point
├── requirements.txt  # Python dependencies
└── .gitignore
```

##  Getting Started

### Prerequisites

- Python 3.10+
- A Google Gemini API key
- Node.js (if the `frontend/` uses a separate JS toolchain — check its own README/package.json)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/singhbhadauriyadevansh9-collab/TEAM-ALPHA---DEVANSH.git
cd TEAM-ALPHA---DEVANSH

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

### Configuration

Create a `.env` file in the project root with your Gemini API credentials:

```env
GEMINI_API_KEY=your_api_key_here
```

### Running the app

```bash
# Start the backend API
uvicorn app:app --reload

# In a separate terminal, start the frontend (if applicable)
cd frontend
npm install
npm run dev
```

The backend will be available at `http://localhost:8000` by default, with interactive API docs at `http://localhost:8000/docs`.

##  How It Works

1. A PDF is uploaded and parsed page-by-page with PyMuPDF.
2. Text chunks are embedded using `sentence-transformers` and stored in a local ChromaDB collection.
3. When generating a brief, relevant chunks are retrieved from ChromaDB and passed to Gemini along with a structured prompt (claims / methods / results / limitations).
4. Gemini's output is checked against the retrieved chunks so each claim can be traced back to its source in the paper.
5. The final output is rendered as a summary, flashcards, and/or presentation notes in the frontend.

##  Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes
4. Push to the branch and open a Pull Request

##  License
No license file is currently included in this repository. Contact the maintainer before reusing this code in another project.
 
##  Team
 
Maintained by **Team Alpha** ([@singhbhadauriyadevansh9-collab](https://github.com/singhbhadauriyadevansh9-collab)).

No license file is currently included in this repository. Contact the maintainer before reusing this code in another project.

## 👥 Team

Maintained by **Team Alpha** ([@singhbhadauriyadevansh9-collab](https://github.com/singhbhadauriyadevansh9-collab)).

