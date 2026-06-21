# Technical Blog Generator

An LLM-powered blog generation app built with **Python**, **LangGraph**, and **Streamlit**.  
It generates technical blog posts from a topic, optionally uses web research for up-to-date content, and can also create and insert images into the final article.

## Features

- Generate technical blog posts from a topic
- Automatically decide whether research is needed
- Use web search for current or recent topics
- Create a structured blog plan before writing
- Generate markdown output
- Optionally generate images/diagrams for the blog
- Download the final blog as a `.md` file or as a zip bundle with images
- View and load previously generated blog files saved in the project folder

## How it works

The app uses a LangGraph workflow:

1. **Router** decides whether the topic needs research
2. **Research** collects relevant web evidence if needed
3. **Orchestrator** creates the blog outline and section plan
4. **Workers** write each section of the blog
5. **Reducer** merges the sections, adds images if needed, and saves the final markdown file

## Project files

- `bwa_backend.py` — LangGraph workflow and blog generation logic
- `bwa_frontend.py` — Streamlit UI
- `requirements.txt` — Python dependencies

## Requirements

- Python 3.10+
- A Hugging Face token
- Optional: Tavily API key for web research

## Installation

```bash
git clone https://github.com/Manav0411/Technical-Blog-Generator.git
cd Technical-Blog-Generator
pip install -r requirements.txt
```

## Environment variables

Create a `.env` file in the project root:

```env
HF_TOKEN=your_hugging_face_token
HF_TEXT_MODEL=meta-llama/Llama-3.1-70B
HF_IMAGE_MODEL=stabilityai/sdxl-turbo
HF_TEXT_ENDPOINT=
HF_IMAGE_ENDPOINT=
TAVILY_API_KEY=your_tavily_api_key
```

### Notes
- `HF_TOKEN` is required
- `TAVILY_API_KEY` is optional, but needed for web research
- `HF_TEXT_ENDPOINT` and `HF_IMAGE_ENDPOINT` are optional custom endpoints

## Run the app

```bash
streamlit run bwa_frontend.py
```

## Usage

1. Enter a blog topic in the sidebar
2. Choose an optional as-of date
3. Click **Generate Blog**
4. Review the plan, evidence, preview, images, and logs
5. Download the final markdown file or zip bundle

## Output

The app saves generated blog posts as `.md` files in the current folder.  
If images are generated, they are saved inside an `images/` folder.

## Dependencies

Main libraries used:

- `streamlit`
- `langgraph`
- `langchain-core`
- `huggingface_hub`
- `pydantic`
- `python-dotenv`
- `pandas`
