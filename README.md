# CVs-Sourcing-Applicant-Tracking

A small app to extract key info from **CVs / LinkedIn screenshots**, optionally compare to a **Job Description (JD)**, and rank candidates with a **weighted score**. Exports a **clean CSV** and **JSON**.

## Features
- Upload multiple files: PDF, DOCX, TXT, RTF, PNG, JPG, JPEG, WEBP
- Optional OCR for images (Tesseract)
- Extracts: name, title, LinkedIn, email/phone, responsibilities, degree, years, skills, GPA, achievements, volunteering
- Weighted scoring (responsibilities, degree, experience, skills, plus/extra skills, GPA, achievements, volunteering)
- Gradio GUI + Top-N preview + CSV/JSON export

## Install
```bash
pip install -U torch transformers sentence-transformers gradio pypdf2 python-docx pillow pytesseract pandas
# (Optional) Tesseract engine for OCR:
# Ubuntu: sudo apt-get install tesseract-ocr
# macOS:  brew install tesseract
# Windows: install from tesseract-ocr project, then set TESSERACT_PATH if needed
```
## Run

Notebook: paste the single cell and run (Gradio renders inline).

Open the local Gradio URL, upload files, (optionally) paste a JD, choose Top N, then Run matching.

## Outputs

- cv_matching_summary.csv — clean columns for quick triage:
rank, filename, linkedin, email, phone, final_score(%)

- cv_matching_results.json — top-N results with extracted features & scores.

## Scoring (weights)

- Responsibilities 0.19,
- Degree 0.19,
- Experience 0.19,
- Skills 0.19,
- Plus 0.05,
- Extra 0.05,
- GPA 0.05,
- Achievements 0.06,
- Volunteering 0.03.

## Tips

- No JD? Leave it blank (neutral matching).

- CSV layout can be edited in build_summary_df(...).

- If OCR text is empty, verify Tesseract is installed / TESSERACT_PATH is set.
