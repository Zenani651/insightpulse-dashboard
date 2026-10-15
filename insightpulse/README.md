# InsightPulse

Smart feedback analytics for customer reviews and comments. A single-page web app that runs entirely in the browser: no server, no build step, no API keys.

## Features

- Upload CSV, Excel (.xlsx/.xls), JSON or text files, or paste reviews directly
- Data cleaning: empty rows, duplicates, HTML, links and extra spaces
- Positive / neutral / negative classification with confidence scores
- Emotion detection (joy, anger, sadness, frustration)
- Aspect-based analysis (service, price, delivery, quality and more)
- Sentiment trends over time, comparisons by product or period
- Configurable alerts, including spikes in negative feedback
- Rating vs sentiment mismatch detection and model evaluation (accuracy, precision, recall, F1, confusion matrix)
- Executive summary, top actions, guided tour and full-screen presentation mode
- Click-through drilldown, search, filters and sorting
- Export to PDF, Excel, Markdown and CSV
- Light and dark mode, five built-in sample datasets

## Run it

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy with GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Your site appears at `https://<your-username>.github.io/<repo-name>/`.

## How the analysis works

Sentiment uses a rule-based word-score model that handles negation ("not good"), intensifiers ("very good"), "but" clauses and exclamation marks. It has a small vocabulary for English plus basic Spanish, French, German and Portuguese. Topics are matched by keywords.

Known limits: sarcasm, slang and mixed feelings can fool the scoring, and unusual wording can be missed by topic matching.

## Features that only work inside Claude

This page was built as a Claude artifact. Three features use Claude-only capabilities and are inactive on GitHub Pages:

- Generate AI insights, Ask AI, and search by meaning
- Saved analysis history

On a normal website these show a short message instead, and everything else works. To enable them outside Claude, connect your own backend that calls an LLM API and replace the `AI` helper (`runAI`, `sem`) in `index.html`. Never put an API key in client-side code.

## Dependencies

Loaded from CDNs: SheetJS (Excel read/write), jsPDF (PDF export) and Google Fonts.

## Project structure

```
index.html   the whole app (HTML, CSS and JavaScript)
README.md    this file
```
