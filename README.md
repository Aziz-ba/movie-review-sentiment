# 🎭 Movie Review Sentiment & Reputation Analysis

An NLP project that measures a film's **online reputation** by scraping **all** of its IMDb user reviews and running each one through a **transformer sentiment model**. The case study is the 2022 film *Babylon*, but the pipeline works for any IMDb title.

Two skills in one project: **dynamic web scraping** (JavaScript "load more" pagination) and **transformer-based NLP**.

---

## 🔬 Pipeline

1. **Scrape** — Selenium drives a headless Chrome to the film's IMDb reviews page and repeatedly clicks *"Load more"* until every review is loaded (reviews are lazy-loaded, so a plain HTTP request isn't enough).
2. **Parse** — BeautifulSoup extracts each review's title and body from the rendered page.
3. **Classify** — each review is scored with a HuggingFace `AutoModelForSequenceClassification` sentiment model (tokenized with the matching `AutoTokenizer`).
4. **Aggregate** — the per-review sentiments roll up into an overall **reputation signal** for the film.

---

## 🧠 Why it's non-trivial

- IMDb reviews are **paginated by JavaScript** → needs a real browser (Selenium), not just `requests`.
- Applying a transformer to **many free-text reviews** and aggregating gives a far richer picture than the single star rating.

---

## 🚀 Run it

```bash
pip install -r requirements.txt
# Requires Chrome + a matching chromedriver on PATH
jupyter notebook notebooks/review_sentiment_analysis.ipynb
```

Change the IMDb `url` at the top of the notebook to analyze a different title.

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=flat-square&logo=selenium&logoColor=white)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4B8BBE?style=flat-square)
![Hugging Face](https://img.shields.io/badge/🤗_Transformers-FFD21E?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)

Python · Selenium · BeautifulSoup · HuggingFace Transformers · PyTorch

---

## 📚 What this project demonstrates

- **Dynamic web scraping** of JavaScript-rendered, paginated content
- Applying a **pre-trained transformer** to real user-generated text
- Turning many noisy reviews into an aggregate, interpretable **reputation metric**

---

## 📄 License

Released under the [MIT License](LICENSE).
