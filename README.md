# ANISF: Evidence-Grounded Bias Mitigation for Trustworthy News Generation

ANISF is a **modular NLP pipeline** designed to improve the reliability
and neutrality of automatically generated news content. The system
integrates **fact verification, evidence retrieval, bias detection, and
controlled text rewriting** to ensure generated news remains **accurate
and unbiased**.

The pipeline verifies factual claims first and only then performs bias
mitigation, ensuring neutrality adjustments do not distort factual
meaning.

------------------------------------------------------------------------

## Motivation

Modern news generation systems face several challenges:

-   Misinformation propagation\
-   Framing bias in reporting\
-   Lack of evidence grounding in automated content

While many systems focus only on **fact verification**, bias detection
and mitigation are often treated separately.

ANISF combines these components into a **single evidence-aware
pipeline** that:

1.  Retrieves supporting evidence\
2.  Verifies factual claims\
3.  Detects framing bias\
4.  Rewrites biased text while preserving factual meaning

This results in **more trustworthy automated news outputs**.

------------------------------------------------------------------------

## System Architecture

    Input Text
        │
        ▼
    Evidence Retrieval (Sentence-BERT + BM25)
        │
        ▼
    Claim Verification (RoBERTa NLI)
        │
        ▼
    Bias Detection (DeBERTa)
        │
        ▼
    Neutral Rewriting (Mistral-7B)
        │
        ▼
    Final Neutral Output

------------------------------------------------------------------------

## Key Components

### Evidence Retrieval

The system retrieves supporting evidence using a **hybrid retrieval
strategy**:

-   Sentence-BERT embeddings for semantic similarity\
-   BM25 ranking for lexical matching\
-   FAISS indexing for efficient vector search

This combination improves both **semantic and keyword-based retrieval
accuracy**.

------------------------------------------------------------------------

### Claim Verification

Retrieved evidence is used to determine whether the claim is:

-   Supported\
-   Refuted\
-   Not enough information

Model used:

-   **RoBERTa-based Natural Language Inference (NLI)**

This ensures the pipeline only processes **verified information**.

------------------------------------------------------------------------

### Bias Detection

Once a claim is verified, the system evaluates whether the text contains
**framing bias**.

Model used:

-   **DeBERTa classifier**

The model identifies linguistic patterns that introduce bias in how
information is presented.

------------------------------------------------------------------------

### Controlled Rewriting

If biased language is detected, the system generates a **neutral version
of the text**.

Model used:

-   **Mistral-7B**

The rewriting module ensures:

-   factual meaning remains unchanged\
-   framing bias is reduced\
-   readability is preserved

------------------------------------------------------------------------

## Technologies Used

**Programming** - Python

**NLP / ML** - Sentence-BERT - RoBERTa - DeBERTa - Mistral-7B

**Retrieval** - FAISS - BM25

**Libraries** - PyTorch - HuggingFace Transformers - Scikit-learn

------------------------------------------------------------------------

## Example Workflow

Example claim:

> "Policy X drastically reduced unemployment across the country."

Pipeline processing:

1.  Evidence is retrieved from relevant documents.\
2.  The NLI model verifies whether the claim is supported.\
3.  The bias detector identifies exaggerated framing.\
4.  The rewriting module generates a neutral version.

Output:

> "Policy X was associated with a reduction in unemployment according to
> available reports."

------------------------------------------------------------------------

## Project Structure

    ANISF/
    │
    ├── retrieval/
    ├── verification/
    ├── bias_detection/
    ├── rewriting/
    ├── pipeline/
    ├── data/
    ├── experiments/
    └── README.md

------------------------------------------------------------------------

## Installation

Clone the repository

``` bash
git clone https://github.com/yourusername/ANISF.git
cd ANISF
```

Install dependencies

``` bash
pip install -r requirements.txt
```

------------------------------------------------------------------------

## Running the Pipeline

``` bash
python run_pipeline.py --input "Your claim text here"
```

The system returns:

-   Retrieved evidence
-   Claim verification result
-   Bias detection result
-   Neutralized output

------------------------------------------------------------------------

## Applications

-   Automated journalism systems\
-   Misinformation detection\
-   Media bias analysis\
-   Trustworthy AI content generation\
-   Research in fact verification and fairness

------------------------------------------------------------------------

## Author

**Akhil Kotnala**\
B.Tech Computer Science\
Graphic Era Deemed to be University
