# Style Finder — Multimodal Retrieval and Search

Style Finder is a prototype application that helps discover visual style and retrieve similar images using multimodal retrieval and LLM-assisted reasoning. The repository contains a small web API/app plus helpers for image processing, retrieval, and LLM integration.

> NOTE: This README was updated to reflect the current repository files and their responsibilities. If you'd like, I can push this change to the repo for you.

## Contents / Project Structure

- `README.md` — This file.
- `app.py` — Entrypoint for the web application / API. Runs the server and exposes endpoints for uploading images and running searches.
- `config.py` — Configuration module. Contains configuration values used across the app (API keys, model names, paths, etc.). Update this file or set the referenced environment variables before running.
- `helpers.py` — Utility functions used by the application (formatting, I/O helpers, maybe embedding/distance helpers).
- `image_processor.py` — Image preprocessing and feature extraction logic. Handles image resizing, normalization, feature computation and any image-to-embedding pipeline calls.
- `llm_service.py` — Integration layer for the large language model(s). Handles prompt construction, calls to the LLM, and post-processing of LLM outputs.
- `requirements.txt` — Python dependencies required to run the project.

## Features (high-level)

- Upload images and produce style / similarity results.
- Multimodal retrieval: image processing + embeddings to find visually or semantically similar items.
- LLM-assisted interpretation: uses a language model to help interpret or summarize style attributes for results.
- Lightweight Flask-style web app for local testing and quick demos.

## Quickstart

1. Clone the repository:
   git clone https://github.com/alankudakkad17/Style-Finder-Using-Multimodal-Retrieval-and-Search.git
   cd Style-Finder-Using-Multimodal-Retrieval-and-Search

2. Create and activate a Python virtual environment (recommended):
   python -m venv .venv
   source .venv/bin/activate  # macOS / Linux
   .venv\Scripts\activate     # Windows

3. Install dependencies:
   pip install -r requirements.txt

4. Configure secrets and settings:
   - Open `config.py` to see the configuration variables used by the app (API keys, model names, storage paths, etc.).
   - Set any required API keys (for example, an LLM provider key) via environment variables or by editing `config.py`. Do not commit secrets to the repository.

5. Run the app:
   python app.py

6. Use the app:
   - By default the app will bind to localhost (commonly http://127.0.0.1:5000). Open your browser to the root endpoint to access the UI or call the API endpoints described in the code.
   - Upload an image or provide a text query to trigger the multimodal retrieval pipeline.

## Configuration & Environment

- The repo uses a small `config.py` module for central configuration. Check that file to learn what environment variables or constants you should set.
- Common config items for this kind of project:
  - API keys for LLMs or external services (set as env vars, referenced by `config.py`).
  - Paths for storing uploaded images, embeddings or caches.
  - Model names or endpoints used by image embedding and LLM services.

## Development notes

- The code is organized to separate concerns:
  - Image preprocessing and feature extraction reside in `image_processor.py`.
  - LLM prompts and calls are in `llm_service.py`.
  - Shared utilities live in `helpers.py`.
  - `app.py` wires the pieces together and exposes the web interface.
- If you want me to add a `Makefile`, Dockerfile, CI workflow, tests, or to push this README update into a branch and open a PR, tell me which you'd prefer and I'll prepare it.

## Contributing

- Feel free to open issues or pull requests against this repo. If you plan to change config or add secrets for CI, prefer repo secrets or environment variables instead of committing keys.

## Troubleshooting

- If the app fails to start, check:
  - That dependencies from `requirements.txt` are installed.
  - `config.py` is correctly set up and any required API keys are available.
  - The server port is not in use.
- Consult the application logs (stdout) for traceback details.

## Contact

- Repository owner: alankudakkad17
- If you want, I can update the README further with examples of API endpoints, sample requests/responses, and exact environment variable names after inspecting the code more deeply or after you grant permission to commit changes.