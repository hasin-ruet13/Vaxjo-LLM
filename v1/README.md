# *Automated Extraction and Classification of Vaccine Adjuvant Immune Mechanisms Using Large Language Models*

---

## Overview

**Vaxjo-LLM** is a scalable, automated pipeline that extracts **vaccine adjuvant names** and their **immune-response mechanisms** from biomedical literature using Large Language Models (LLMs).
It functions as a **Curation Co-Pilot**, helping expert curators maintain and update the Vaxjo vaccine adjuvant database.

The workflow transforms **unstructured biomedical text** into structured, consistent, and searchable mechanistic insights.

---

## Research Objectives

* Automatically extract adjuvant names and immune mechanisms from PubMed abstracts
* Summarize mechanisms with structured evidence
* Analyze mechanistic patterns and co-occurrences
* Identify *novel adjuvants* missing from existing databases
* Assist human curators using a human-in-the-loop workflow

---

## Pipeline Workflow

### **1. Literature Retrieval**

* Query PubMed or provide PMIDs
* Download abstracts or full text when available

### **2. Phase I — Mechanism Extraction**

LLMs identify:

* Adjuvants
* Mechanistic descriptions
* Supporting evidence references

**Example Output (JSON):**

```json
[
  {
    "adjuvant": "Alum",
    "immune_response_mechanism": "Activates NLRP3 inflammasome and promotes slow antigen release."
  }
]
```

### **3. Grouping**

Mechanisms grouped by adjuvant for consistency.

### **4. Phase II — Mechanism Summarization**

LLMs generate structured mechanism summaries:

```json
{
  "adjuvant": "MPLA",
  "summary": "Stimulates TLR4 signaling, activating dendritic cells and promoting Th1 polarization.",
  "mechanism_types": [
    {
      "mechanism_type": "TLR4 activation",
      "evidence_refs": ["18479788"]
    }
  ]
}
```

### **5. Mechanism Pattern Analysis**

* Frequency analysis
* Co-occurrence networks
* Innate vs. adaptive pathway distribution

### **6. Novel Adjuvant Detection**

The pipeline flagged **27 novel adjuvants** not included in existing databases — demonstrating its value as a discovery and curation tool.

---

## Curation Co-Pilot (Proof-of-Concept)

An LLM-powered interface that enables curators to:

* View extracted adjuvant–mechanism pairs
* Compare with database entries
* Accept, reject, or correct LLM outputs
* Generate ontology-ready annotations

This is a step toward a fully integrated **AI-assisted curation ecosystem**.

---

## Repository Structure

```
Vaxjo-LLM/
├── Prompts/        # LLM prompts for each extraction/summarization phase
├── Datasets/       # Input literature, PMC text, curated datasets
├── Outputs/        # JSON outputs, summaries, plots, aggregated data
├── v0/             # Archived older version of the project
├── *.ipynb         # Pipeline notebooks (Phase I, Phase II, analysis)
└── README.md
```

---

## How to Run

### **1. Install Dependencies**

(Optional — if requirements file exists)

```bash
pip install -r requirements.txt
```

### **2. Launch Jupyter Notebook**

```bash
jupyter notebook
```

### **3. Run the notebooks in sequence:**

1. Extract PMID and download papers.ipynb
2. Llama Inferencing_Vaxjo.ipynb
3. Output Conversion.ipynb
4. Mechanism summary and subtype.ipynb
5. Regroup and plot.ipynb
6. Regroup Surface and plot.ipynb
7. Final Adjuvant list and novel.ipynb

---

## Contact

**Hasin Rehana**
Ph.D. Student, UND
📧 [hasin.rehana@und.edu](mailto:hasin.rehana@und.edu)
🔗 GitHub: [https://github.com/hasin-ruet13](https://github.com/hasin-ruet13)
🌐 Website: [https://hasin-ruet13.github.io/hasinrehana.github.io/](https://hasin-ruet13.github.io/hasinrehana.github.io/)
