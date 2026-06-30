# Indian Government Schemes Finder

Indian Government Schemes Finder is a Flask-based web application that helps users discover relevant government schemes using profile-based filters, keyword search, multilingual translation, and an AI-powered chatbot.

The app uses a local CSV dataset of Indian government schemes and provides details such as eligibility, benefits, required documents, and application steps.

## Highlights

- Profile-based scheme filtering
- Keyword-based search with relevance scoring
- Detailed scheme information pages
- Gemini-powered chatbot for scheme-related questions
- Multilingual page translation using Google Translate
- CSV-backed dataset for simple data updates
- Lightweight Flask application suitable for local use or deployment

## Demo Flow

1. Open the home page.
2. Go to the search page.
3. Search by keyword or select filters such as age, gender, occupation, income, caste, and state.
4. Open a matched scheme to view full details.
5. Use the chatbot to ask natural-language questions about schemes.

## Tech Stack

- **Backend:** Flask
- **Data Handling:** Pandas
- **AI Chatbot:** Google GenAI SDK / Gemini
- **Frontend:** HTML, CSS, JavaScript
- **Dataset:** CSV

## Project Structure

```text
.
|-- app.py
|-- indianschemes.csv
|-- requirements.txt
|-- README.md
|-- static/
|   |-- schemesfinder.jpg
|   `-- translate.png
`-- templates/
    |-- home.html
    |-- index.html
    `-- scheme.html
```

## Getting Started

### Prerequisites

Make sure you have the following installed:

- Python 3.9 or newer
- pip
- A Gemini API key, only required for chatbot responses

## Installation

Clone the repository:

```bash
git clone <your-repository-url>
cd "GOVT SCHEMES FINDER"
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

For Windows PowerShell:

```bash
.\.venv\Scripts\Activate.ps1
```

For macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Environment Variables

The chatbot uses Gemini. Set your Google API key before running the app:

Windows PowerShell:

```bash
$env:GOOGLE_API_KEY="your_api_key_here"
```

macOS/Linux:

```bash
export GOOGLE_API_KEY="your_api_key_here"
```

You can create a Gemini API key from Google AI Studio:

```text
https://aistudio.google.com/
```

The app can still run without this key, but chatbot responses will not work until the key is configured.

## Run Locally

Start the Flask development server:

```bash
python app.py
```

Open the app in your browser:

```text
http://127.0.0.1:5000/
```

## Application Routes

| Route | Description |
| --- | --- |
| `/` | Home page |
| `/search` | Search and filter schemes |
| `/scheme/<scheme_id>` | Scheme details page |
| `/chat` | Chatbot API endpoint |

## Dataset

The app expects a file named `indianschemes.csv` in the project root.

The code automatically detects columns related to:

- Scheme name
- Age
- Gender
- Occupation or category
- Income
- Region or state
- Caste
- Description
- Benefits
- Eligibility
- Application steps
- Required documents
- Scheme level
- Tags or keywords

For best results, keep the `Tags` column updated with useful search keywords for each scheme.

## How Search Works

The app supports two search modes:

- **Filter search:** Matches schemes against selected user profile fields.
- **Keyword search:** Scores schemes based on matches in tags, scheme names, descriptions, eligibility, and occupation fields.

The chatbot also uses keyword-based retrieval to find the most relevant schemes, then sends that context to Gemini for a conversational answer.

## Deployment

`gunicorn` is included in `requirements.txt` for deployment on platforms that support Python web apps.

Example production command:

```bash
gunicorn app:app
```

Remember to configure the `GOOGLE_API_KEY` environment variable on your hosting platform if you want chatbot support.

## Notes

- The CSV file is read using `latin1` encoding.
- The Google Translate widget requires browser internet access.
- Do not commit real API keys to GitHub.
- Keep `indianschemes.csv` in the project root unless you update the path in `app.py`.

## Author

Created as a government scheme discovery project to make welfare information easier to search and understand.
