# COVID-19 and health topics in European Parliament Debated (2020) (NLP, LLM-BASED EXTRACTION, KG, NETWORK)

## Overview
This project analyzes health-related discussions in European Parliament debates during the year 2020, with a particular focus on COVID-19 and public health issues.  
The study applies **Large Language Models (LLMs)** for structured information extraction and combines **descriptive analysis** with **knowledge graph and network analysis** to explore how political parties discussed health topics during the pandemic.

The project demonstrates a complete analytical pipeline, from raw text data to structured insights and network-based representations.

---

## Purpose
The main objectives of this project are:
- To identify whether parliamentary speeches mention COVID-19 or health-related issues in 2020
- To extract key health topics using an LLM-based approach
- To compare health-related discourse across political parties
- To model relationships between political parties and health topics using a knowledge graph
- To analyze the network structure of health-related political discourse

---

## Dataset
- **Original Source:** EU debates (Parliament speeches) (https://huggingface.co/datasets/RJuro/eu_debates)
- **Time period Scope:** Year 2020  
- **Unit of analysis:** Individual speeches  
- **Key variables:**
  - `speaker_party`
  - `analysis_text` (translated text when available, otherwise original English text)
  - LLM-extracted labels (health mention, health topics)

---

## Project Pipeline

### Step 0: Data Loading & Initial Exploration
- Load debate transcripts into a pandas DataFrame
- Filter debates from the year 2020
- Create a unified `analysis_text` column using:
  - English translated text when available
  - Original English text as fallback
- Perform basic dataset exploration (row counts, party distribution)

---

### Step 1: Rule-based & Keyword Exploration (Baseline)
- Conduct preliminary keyword-based checks for health-related terms
- Use this step to:
  - Understand the data
  - Motivate the need for an LLM-based approach
- No final labels are assigned at this stage

---

### Step 2: LLM-based Structured Extraction
- Use a locally deployed LLM (via **Ollama – Gemma 3 4B**) to process speeches
- The LLM is prompted to return **strict JSON output**:
  ```json
  {
    "health_mentioned": true or false,
    "health_topics": ["list of health-related topics"]
  }

  ---

### Step 3: Descriptive Analysis
- Analyze the proportion of health-related speeches
- Compare health-related discourse across political parties
- Identify the most frequently mentioned health topics
- Visualizations include:
  - Proportion bar charts
  - Party-level comparison plots
  - Topic frequency bar charts
  - Party–topic heatmap

---

### Step 4: Knowledge Graph Construction
- Construct a bipartite knowledge graph using NetworkX
- Nodes:
  - Political parties
  - Health topics
- Edges:
  - Represent mentions of a health topic by a party
- Weighted by frequency of mentions
- The graph visualizes the structure of health-related discourse in 2020

---

### Step 5: Network Analysis
- Apply network metrics, including:
- Degree centrality
- Weighted degree centrality
- Identify:
  - Dominant political parties in health-related discussions
  - Central health topics during the pandemic
  - Interpret results in relation to EU political dynamics during COVID-19

### Key Findings (Summary)
- Around one-third of parliamentary speeches in 2020 addressed health-related issues
- Healthcare systems were discussed more frequently than COVID-19 itself
- Large political groups (e.g., PPE and S&D) dominated health-related discourse
- Knowledge graph analysis highlights strong connections between major parties and core health topics

## Limitations
- LLM outputs may contain classification errors or topic ambiguity
- Topic granularity depends on prompt design
- Analysis is limited to one year (2020)
- Results should be interpreted as exploratory rather than causal

## Future Work
- Extend the analysis to multiple years for comparison
- Compare LLM-based extraction with traditional NLP methods
- Improve topic normalization and clustering
- Use interactive graph visualizations (e.g., PyVis)

## Technologies Used
- Python: pandas, matplotlib, seaborn, NetworkX
- Ollama (Gemma 3:4B)
- Jupyter Notebook / Google Colab

## Author
- Suchanya Baiyam
- This project was developed as part of an academic assignment on LLM-based text analysis and knowledge graph construction at AAU
