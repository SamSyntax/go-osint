# Go OSINT Article Analyzer

## Why This Project Exists

A friend was given an assignment to detect and assess the level of propaganda in various media, such as social media posts and news articles. The professor provided a list of open-source intelligence (OSINT) tools, but many were outdated, no longer functional, or simply not up to the task.

This project was created to provide a modern and effective solution. Instead of relying on a collection of disparate tools, this analyzer offers a streamlined workflow to gather, process, and analyze content for potential propaganda.

## What It Does

This tool is an article analyzer designed to:

1.  **Fetch Articles**: Gather articles from various sources based on a specific subject.
2.  **Tokenize Content**: Process and break down the text of the collected articles into a structured format.
3.  **AI-Powered Assessment**: Feed the tokenized content to an AI model to assess the propaganda level across the entire corpus of articles.

The goal is to provide a more holistic and data-driven perspective on how a particular subject is being portrayed in the media.

## Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/SamSyntax/go-osint
    cd go-osint
    ```

2.  **Build the application:**
    ```bash
    make build
    ```

## Configuration

1.  **Create a `.env` file:**
    ```bash
    cp .env.example .env
    ```

2.  **Edit the `.env` file:**
    Open the `.env` file and add your API keys:
    ```
    NEWS_API_KEY="your_news_api_key"
    HUGGINGFACE_API_KEY="your_huggingface_api_key"
    ```

## Usage

There are two main ways to use the application:

### 1. Fetch and Analyze Articles

This command will fetch articles about "Syrian War", save them to `osint.json`, and then analyze them for propaganda. The results will be saved in `labeled_articles.json` and a summary report will be generated in `summary.md`.

```bash
make run
```

You can also specify a different query:

```bash
./bin/osint -query="your query"
```

### 2. Analyze Local Articles

If you already have a JSON file with articles (in the same format as `osint.json`), you can analyze it directly:

```bash
./bin/osint -input="path/to/your/articles.json"
```

### 3. Scrape Articles Only

If you only want to scrape the content of the articles without performing any analysis, use the `-onlyScrape` flag. The scraped content will be saved to `scrape.json`.

```bash
./bin/osint -onlyScrape
```

You can specify a different output file:

```bash
./bin/osint -onlyScrape -o="path/to/your/scraped_articles.json"
```

### Command-line Flags

*   `-newsApiKey`: API key for News API. Can also be set via the `NEWS_API_KEY` environment variable.
*   `-query`: The query to search for articles. Defaults to "Syrian War".
*   `-hgfApiKey`: API key for Hugging Face API. Can also be set via the `HUGGINGFACE_API_KEY` environment variable.
*   `-onlyScrape`: If set, only scrapes articles without calling any APIs. Defaults to `false`.
*   `-o`: Path to save scraped articles. Defaults to `./scrape.json`.
*   `-input`: Path to an input JSON file with articles. Defaults to `./osint.json`.

## Disclaimer

This tool uses AI to assess content, and its analysis should be considered a starting point for further investigation, not a definitive judgment. The "propaganda level" is a complex and subjective metric, and the AI's assessment is based on the patterns it has learned from its training data. Always use critical thinking and cross-reference with multiple sources. In short, don't be a dum dum, thanks.
