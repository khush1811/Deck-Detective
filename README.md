# Deck-Detective

---

# **PPTX Inconsistency Detector**

## **Overview**

This Python tool uses **Google Gemini 2.5 Flash** to automatically detect factual, numerical, and logical inconsistencies across slides in a PowerPoint presentation.
It works with any `.pptx` file and identifies issues such as:

* **Conflicting numerical data** (e.g., revenue figures that don’t match, incorrect percentage totals)
* **Contradictory textual claims** (e.g., “market is highly competitive” vs “few competitors”)
* **Timeline mismatches** (e.g., inconsistent forecast dates)

The script processes each slide's text, sends it to the Gemini API, and outputs a **structured JSON-like summary** of the inconsistencies, referencing the slide numbers where they occur.

---

## **Features**

* **Multi-slide processing** — reads text from all slides in `.pptx` presentations.
* **Text-based inconsistency detection** — flags both **numerical** and **logical/textual** contradictions.
* **Structured output** — returns results as a JSON list containing:

  * `slide_number` — the slide(s) where the issue occurs
  * `issue_description` — a clear explanation of the inconsistency
* **Uses Google Gemini 2.5 Flash** — ensures fast and accurate AI analysis.
* **Generalized approach** — works with any presentation, not just the sample deck provided.

---

## **Installation & Setup**

### **1. Clone this repository**

```bash
git clone https://github.com/yourusername/pptx-inconsistency-detector.git
cd pptx-inconsistency-detector
```

### **2. Install dependencies**

```bash
pip install python-pptx pillow pymupdf requests google-generativeai
```

### **3. Set up your Gemini API key**

Get a free API key here: [Google AI Studio](https://aistudio.google.com/app/apikey)

Export it as an environment variable:

```bash
export GEMINI_API_KEY="your_api_key_here"
```

*(Windows PowerShell)*:

```powershell
setx GEMINI_API_KEY "your_api_key_here"
```

---

## **Usage**

Run the script with:

```bash
python detect_inconsistencies.py
```

Example output:

```json
[
  {
    "slide_number": "1 and 2",
    "issue_description": "Conflicting financial impact figures: Slide 1 states '$2M' impact, while Slide 2 claims '$3M saved in lost productivity hours annually'."
  },
  {
    "slide_number": "3",
    "issue_description": "Numerical inconsistency: The stated total of '50 Hours Saved Per Consultant Monthly' contradicts the sum of time-saving categories (40 hours)."
  }
]
```

---

## **Code Structure**

* **`extract_text_from_pptx(file_path)`** — Reads and extracts text from each slide.
* **`analyze_inconsistencies(slide_texts)`** — Sends the extracted text to Gemini for analysis, asking for structured JSON output.
* **`main`** — Loads the `.pptx` file, runs the analysis, and prints results.

---


## **License**

This project is licensed under the MIT License.

---
