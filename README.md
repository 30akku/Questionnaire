# Questionnaire

Desktop revision assistant that extracts text from study material images and generates practice questions for students.

Repository: https://github.com/30akku/Questionnaire

## What It Does

Questionnaire is a Python desktop application for turning study material into revision questions. A student uploads an image containing text, the app extracts the text with OCR, sends it to a question-generation API, and presents generated practice material through a GUI.

The application supports short-answer questions, fill-in-the-blank questions, quiz-style practice, score checking, and PDF export for offline revision.

## Key Features

- Desktop GUI built with Qt.
- Image upload flow for study material.
- OCR-based text extraction using Tesseract.
- Question generation through the Quillionz API.
- Short-answer question generation.
- Fill-in-the-blank practice mode.
- Score/check-answer workflow.
- PDF export for generated short-answer questions.
- Included screenshots and demo video link.

## Tech Stack

- Python
- PySide2 / Qt Designer
- OpenCV
- Tesseract OCR / pytesseract
- Requests
- FPDF
- Quillionz API

## Project Structure

```text
.
|-- main.py              # Main PySide2 application and question-generation flow
|-- app_functions.py     # Application function wrapper
|-- ui_main.py           # Generated main UI code
|-- ui_splash_screen.py  # Generated splash screen UI code
|-- ui_functions.py      # UI behavior helpers
|-- ui_styles.py         # UI style definitions
|-- *.ui                 # Qt Designer files
|-- Screenshot (*.png)   # App screenshots
`-- question_sa.pdf      # Example generated PDF
```

## How It Works

1. The user opens the desktop application.
2. The user uploads an image containing study text.
3. OpenCV preprocesses the image and Tesseract extracts text.
4. Extracted text is sent to the Quillionz question-generation API.
5. Generated short-answer and fill-in-the-blank questions are shown in the app.
6. The user can practice answers, check score, or export short-answer questions to PDF.

## Getting Started

### Prerequisites

- Python
- Tesseract OCR installed locally
- A valid Quillionz API configuration, if the public endpoint/key behavior changes

Install Python dependencies:

```bash
pip install PySide2 opencv-python pytesseract requests fpdf
```

The original README also mentions `pyqt5`, `pyqt5-tools`, and `asyncio`; the current `main.py` imports PySide2 directly.

### Configure Tesseract

`main.py` currently points to a Windows Tesseract installation:

```python
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files (x86)\Tesseract-OCR\tesseract"
```

Update this path if Tesseract is installed somewhere else on your machine.

### Run

```bash
python main.py
```

## Demo

Video demo from the original README:

https://youtu.be/mHtdlezY2K4

## Screenshots

### Upload Image

![Upload image screen](https://user-images.githubusercontent.com/54696902/92317940-ab7f7500-f023-11ea-9031-0a72ee4e26e4.png)

### Practice Test

![Practice test screen](https://user-images.githubusercontent.com/54696902/92318200-6c9eee80-f026-11ea-9e61-80501b01a5e7.png)

### Check Answers

![Check answers screen](https://user-images.githubusercontent.com/54696902/92318048-9a833380-f024-11ea-8148-5194b4f88230.png)

### Short Answer Questions

![Short answer screen](https://user-images.githubusercontent.com/54696902/92317951-b9cd9100-f023-11ea-806f-d1fca8e26126.png)

## Future Improvements

- Add a `requirements.txt` with pinned versions.
- Move API endpoint and credentials to environment variables.
- Add error handling for OCR failures, API failures, and empty image uploads.
- Package the desktop app for easier installation.
- Split OCR, API, PDF, and UI logic into smaller modules.
