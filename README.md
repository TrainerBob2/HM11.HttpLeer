# HM11.HttpLeer

It ingests normalized HTTP request data , embeds requests using sentence transformers, clusters similar behavior, and **prioritizes potentially interesting security issues** such as SSRF, IDOR, debug leaks.

AKA “Show me the weird, rare, and dangerous-looking endpoints first.”

---

## Features

- Semantic embeddings of HTTP traffic using `sentence-transformers`
- Clustering to identify common vs rare behaviors
- Bug-class similarity scoring using curated seed phrases
- Risk-based scoring system with adjustable boosts and penalties
- Outputs a machine-readable `analysis_results.json`
- Streamlit UI for interactive analysis

---

## Detection Philosophy

### 1. Semantic similarity
- Each request is embedded and compared against bug seed embeddings
- Supports SSRF, IDOR, CRUD/write ops, debug/error leakage

### 2. Behavioral rarity
- Rare clusters and outliers are boosted
- Small clusters are treated as suspicious by default

### 3. Security heuristics
- Write methods (POST/PUT/DELETE) increase score
- Error/debug keywords increase score
- Auth-required endpoints are slightly deprioritized

This approach mirrors how experienced pentesters think during reconnaissance.

---
# Install dependencies

```pip install sentence-transformers scikit-learn hdbscan streamlit pandas numpy```


