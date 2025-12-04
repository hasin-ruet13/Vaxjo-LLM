The `Vaxjo-LLM-2Phase-End2EndPipeline.ipynb` notebook implements a two-stage LLM workflow:

1. **Phase I – Adjuvant & mechanism extraction from PubMed abstracts**
   - Reads a JSON file of PubMed articles (`{PMID: {title, abstract}}`).
   - Uses Llama 3.2 with a structured prompt to extract:
     - vaccine **adjuvant names**
     - associated **immune-response mechanism** descriptions.
   - Saves raw LLM responses to text and logs per-PMID status to CSV.

2. **Intermediate – Canonicalization & collapsing**
   - Maps variant adjuvant names to **canonical labels**.
   - Collapses multiple papers into a single row per adjuvant with aggregated mechanism text.

3. **Phase II – Mechanism summarization and structuring**
   - For each canonical adjuvant, uses Llama again to:
     - generate a multi-sentence **mechanistic summary**.
     - extract structured **mechanism subtypes** with supporting PMIDs.
   - Writes outputs to both human-readable `.txt` and machine-friendly `.jsonl` files in `Outputs/`.
4. **Postprocessing & analysis**
   - Normalizes mechanism subtypes and assigns them to **standardized mechanism families**.
   - Builds an **adjuvant × mechanism-family matrix** for downstream analysis.
   - Computes mechanism-family frequencies and (optionally) generates visualizations such as:
     - mechanism family **pie chart**
     - top-20 adjuvant **mechanism heatmap**
