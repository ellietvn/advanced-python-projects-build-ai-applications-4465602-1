# Copilot Instructions

## Repository purpose

- This is a LinkedIn Learning course repository containing paired `Begin/` (learning starters) and `Finish/` (reference implementations) Python projects.
- Keep the instructional purpose clear. Preserve comments and checkpoints in starter files unless the requested change explicitly modernizes or completes a lesson.
- Treat `Finish/` as the completed implementation to use for behavioral reference, not as a file that should be copied blindly into `Begin/`.
- Do not rewrite the repository into a production framework or add unrelated tooling. Small, focused changes are preferred.

## Course structure

- `Begin/CH_0_OOP_Refresher.py` and `Finish/CH_0_OOP Refresher.py`: Python class basics.
- `Begin/CH_1_NLP_ChatBot.py` and `Finish/CH_1_NLP_ChatBot.py`: rule-based/TextBlob chatbot.
- `Begin/CH_2_Business_Prediction.ipynb` and `Finish/CH_2_Business_Prediction.ipynb`: pandas/scikit-learn regression exercise.
- `CH_3_DocuChat_Backend.py` and `CH_3a_Challenge.py`: FastAPI and AWS/MongoDB document upload exercises.
- `CH_4_DocuChat_Frontend.py` and `CH_4a_Challenge.py`: Streamlit frontends that call the backend.
- Supporting datasets include `Coffee_shop_data.xlsx` and `population.csv` in both folders.

## Working conventions

- Make changes only in the folder(s) requested. When updating a `Begin/` starter, preserve the exercise structure and TODO-style scaffolding unless asked to implement the full solution.
- When updating a corresponding `Finish/` file, keep it runnable and aligned with the course's reference behavior.
- If a change belongs in both folders, apply it coherently but do not turn an exercise into the finished implementation in `Begin/`.
- Match nearby naming and formatting. Existing code is intentionally educational and often not fully formatted; do not perform repository-wide cleanup.
- Use clear names, docstrings for non-obvious functions, and standard library types or Pydantic models where appropriate.
- Keep imports scoped to the file that uses them and remove imports only when the change makes them unused.

## Dependencies

- The root `requirements.txt` is a placeholder and normally should remain unchanged.
- Chapter-specific dependencies live in `Begin/CH_3_Requirements.txt`, `Begin/CH_4_Requirements.txt`, and their `Finish/` counterparts.
- Update the relevant chapter requirements file when adding a package; do not add packages globally without a manifest change.
- Major stacks:
  - Chapter 1: TextBlob.
  - Chapter 2: pandas, scikit-learn, matplotlib, numpy, openpyxl-compatible Excel support.
  - Chapter 3: FastAPI, Uvicorn, Pydantic, LangChain packages, FAISS, MongoDB/PyMongo, boto3/awswrangler.
  - Chapter 4: Streamlit and requests.

## Configuration and external services

- Never commit API keys, AWS credentials, MongoDB connection strings, or other secrets.
- Preserve environment-variable and placeholder patterns (`OPENAI_API_KEY`, AWS variables, MongoDB URLs) instead of hardcoding real credentials.
- For local Windows development, `.env` loading may be used; for Codespaces/Linux, prefer environment variables.
- The document-chat frontend contains a Codespaces URL and should not be generalized or replaced unless the task requires configuration changes.
- AWS S3 and MongoDB operations may require external services. Add guards or configuration checks rather than claiming a successful external operation in offline tests.

## Running and validating

- There is no single automated test suite or standard build script in this repository.
- Run the smallest relevant check:
  - `python <file>.py` for a standalone script.
  - `uvicorn Begin.CH_3_DocuChat_Backend:app --reload` or `uvicorn Finish.CH_3_DocuChat_Backend:app --reload` for the chapter 3 backend.
  - `streamlit run Begin/CH_4_DocuChat_Frontend.py` or `streamlit run Finish/CH_4_DocuChat_Frontend.py` for the chapter 4 UI.
- Run `python -m py_compile <changed-file>` to catch syntax errors. Be aware that intentionally incomplete `Begin/` files may not be syntactically executable; validate them only when completing the corresponding exercise.
- Notebook changes should remain valid JSON and preserve the learning flow. Run edited cells or the notebook end-to-end when the environment and datasets permit.
- Before the final response, inspect the diff and run the narrowest relevant validation. Do not run external API, AWS, or MongoDB calls unless credentials and test resources are available.

## Data and file handling

- Resolve chapter files relative to the directory in which the script/notebook is run, and avoid hardcoding an instructor-specific absolute path.
- Use the upload filename rather than trusting client-provided paths; guard file types and temporary file cleanup.
- Close uploaded files and remove temporary downloads after use.
- Preserve the existing sample datasets and do not regenerate or modify them for unrelated source changes.

## Pull requests and review

- The repository explicitly does not accept pull requests; `CONTRIBUTING.md` says all PRs will be closed.
- Do not create or modify a pull request unless the user explicitly asks for one and understands the repository policy.
- Explain validation limitations when external credentials or services are unavailable.
