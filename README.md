```{=html}
<p align="center">
```
`<img src="docs/images/17a1c3f5-c9f5-4964-b9e1-fda6de38d408.png" width="1000" />`{=html}
```{=html}
</p>
```
```{=html}
<h1 align="center">
```
📚 Deep Read Agent
```{=html}
</h1>
```
```{=html}
<p align="center">
```
An Open-Source AI Research Assistant`<br>`{=html} Discover papers →
Extract full PDFs → Generate deep insights → Sync to Notion
```{=html}
</p>
```

------------------------------------------------------------------------

# 🚀 Overview

Deep Read Agent is an open-source research automation tool that
transforms academic paper discovery into a structured AI-powered
workflow.

It automatically:

-   🔍 Searches recent papers (arXiv + optional HuggingFace)
-   📊 Ranks papers by recency, citations, and keyword relevance
-   📄 Downloads and extracts full PDF content
-   🧠 Generates structured deep-reading insights using an LLM
-   📝 Saves results into a Notion database (with deduplication)

This project turns scattered research reading into a scalable knowledge
system.

------------------------------------------------------------------------

# 🏗 Architecture & Workflow

::: {align="center"}
`<img src="docs/images/17a1c3f5-c9f5-4964-b9e1-fda6de38d408.png" width="900" />`{=html}
:::

------------------------------------------------------------------------

# 🧠 Example Output Structure

Each analyzed paper generates:

-   🔥 Recommendation Level
-   📌 Deep Summary
-   🧪 Methods & Experimental Design
-   💡 Key Innovations & Contributions
-   🛠 Improvement Ideas (If I Were to Extend This Work)

------------------------------------------------------------------------

# 📦 Core Modules

## 1️⃣ ask_config()

Configures:

-   Time range (7 / 30 / 90 / 180 days)
-   Number of papers to deeply analyze
-   Topic keywords

Default:

``` json
{
  "time_range_days": 30,
  "deep_read_count": 2
}
```

------------------------------------------------------------------------

## 2️⃣ discover_and_extract()

Responsibilities:

-   Search arXiv
-   (Optional) Fetch citation counts
-   Rank papers
-   Download PDFs
-   Extract full text
-   Chunk text (≤10 chunks)

Returns structured paper objects ready for analysis.

------------------------------------------------------------------------

## 3️⃣ save_to_notion()

Saves structured results to a Notion database.

Required Notion database fields:

  Field Name              Type
  ----------------------- -----------
  Title                   title
  Paper URL               url
  Recommendation          select
  Deep Summary            rich_text
  Methods & Experiments   rich_text
  Key Innovations         rich_text
  Improvement Ideas       rich_text

------------------------------------------------------------------------

# 🧮 Ranking Algorithm

Score combines:

-   Keyword match weight
-   Recency boost
-   log10(citationCount)

Formula:

    score = keyword_score + recency_score + log10(citationCount)

------------------------------------------------------------------------

# 🛠 Installation

Node.js \>= 18 recommended

``` bash
npm install
```

Dependencies:

-   node-fetch
-   pdf-parse
-   zod

------------------------------------------------------------------------

# ▶️ Usage

## Step 1: Configure

``` js
await ask_config()
```

## Step 2: Discover & Extract

``` js
await discover_and_extract({
  topic: "LLM inference efficiency",
  time_range_days: 30,
  deep_read_count: 2
})
```

## Step 3: Run LLM Analysis

Generate structured deep insights using your preferred LLM.

## Step 4: Save to Notion

``` js
await save_to_notion({
  notion_api_key: "...",
  notion_database_id: "...",
  items: [...]
})
```

------------------------------------------------------------------------

# 🔐 Security

-   No API keys are stored
-   No credential persistence
-   Runtime-only authentication
-   No sensitive data logging

------------------------------------------------------------------------

# 🌟 Why This Project Matters

Traditional research workflows:

-   Manual filtering
-   Surface-level reading
-   Disorganized notes

Deep Read Agent enables:

-   Automated discovery
-   Full-text understanding
-   Structured knowledge capture
-   Long-term research intelligence

This is a foundation for building a scalable AI Research OS.

------------------------------------------------------------------------

# 📈 Roadmap

-   [ ] OpenAlex integration
-   [ ] Local PDF ingestion
-   [ ] Embedding-based deduplication
-   [ ] Automated research roadmap generation
-   [ ] Multi-database export support

------------------------------------------------------------------------

# 📜 License

MIT

------------------------------------------------------------------------

# ⭐ Support

If this project helps your research:

Star ⭐\
Fork 🍴\
Contribute 🚀

Let's build open research intelligence.
