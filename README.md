# VERIRAG: Verification-Enhanced Retrieval-Augmented Generation

A Self-Disagreement-Aware Retrieval-Augmented Generation system that detects conflicting evidence in documents and provides multi-view answers with calibrated confidence scores. Unlike traditional RAG systems that collapse disagreement into falsely confident responses, VERIRAG explicitly surfaces conflicts, quantifies uncertainty, and shows *where* sources disagree.
 
## Features

- Automatic Conflict Detection - Identifies contradictions at the claim level
- Disagreement Graphs - Visualizations showing which claims support or conflict
- Calibrated Confidence - Adjusts confidence (high/medium/low) based on source agreement
- Multi-View Synthesis - Presents dominant view + alternative perspectives
- Quantitative Metrics - Disagreement density, conflict ratio, entropy scores
- Multi-Format Support - Works with PDF, DOCX, PPTX, TXT, MD, CSV
- Dual-Model Architecture - Fast extraction (Local Llama3) + quality synthesis (Local Phi3 Mini)
- Transparent Reasoning - See exactly why the system is confident or uncertain

### Conflict Detection Process

1. Claim Extraction: Breaks down each retrieved document chunk into atomic factual claims
2. Pairwise Analysis: Compares claims to detect entailment, contradiction, or neutrality
3. Graph Construction: Builds a network where nodes are claims and edges represent relationships
4. Metric Computation: Calculates disagreement density, conflict ratio, and confidence entropy
5. Confidence Calibration: Adjusts system confidence based on quantitative disagreement metrics

### System Architecture

```
Query → Vector Retrieval (Top-K Chunks, via LlamaIndex) → Claim Extraction (via Llama3) → Relationship Analysis (via Llama3) → Disagreement Graph Construction (NetworkX + Metrics) → Multi-View Synthesis (via Phi3:mini) → Calibrated Answer + Visualizations
```

### Use Cases

- Research & Academia: Detect conflicting findings, verify claims, and surface research gaps
- Education & Study: Highlight disputed concepts to focus on deeper conceptual understanding
- Legal & Medical: Identify precedent splits, guideline disagreements, and decision risk
- Journalism & Verification: Cross-check sources, flag contradictions, and expose framing bias

## How to Run

1. Make sure you have Python 3.8+ installed.
2. Clone this repository on your local machine.
3. Install the required dependencies:
```bash
pip install llama-index llama-index-llms-ollama llama-index-embeddings-huggingface sentence-transformers numpy pandas matplotlib seaborn networkx scikit-learn pypdf python-pptx python-docx nltk transformers torch
```
4. Set up the Corpus folder in the project directory, add the relevant files to this folder; the system will be working with this folder. Name the folder 'documents'.
5. Install Ollama & set up llama3:latest & phi3:mini.
6. Open and run the cells of the `VERIRAG System.ipynb` Jupyter Notebook, ask the relevant queries.

## Contributing

Contributions are welcome!

## License

Distributed under the MIT License. 
