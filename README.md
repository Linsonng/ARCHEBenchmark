# ARCHE: Latent Reasoning Chain Extraction

[![Paper](https://img.shields.io/badge/Paper-AAAI%202026-blue)](https://arxiv.org/abs/2511.12485)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-green.svg)](https://creativecommons.org/licenses/by/4.0/)

> *"All valid reasoning is either deductive, inductive, or hypothetic; or else it combines two or more of these characters."*
> — Charles S. Peirce

## Overview

**ARCHE (Latent Reasoning Chain Extraction)** is a novel benchmark and task designed to evaluate how well large language models (LLMs) can understand and formalize the fundamental reasoning paradigms underlying scientific argumentation. While LLMs can produce reasoning-like content through methods such as chain-of-thought prompting, these outputs are typically unstructured and informal, making it unclear whether models truly grasp the elementary inference modes that underpin rigorous scientific discourse.

ARCHE addresses this gap by requiring models to:
1. **Recognize** distinct reasoning paradigms (deduction, induction, abduction)
2. **Extract** fine-grained reasoning steps from scientific texts
3. **Formalize** these steps into a structured **Reasoning Logic Tree (RLT)**

## Key Features

### 🎯 Task: Latent Reasoning Chain Extraction

Given a scientific paper's *introduction* and cited abstracts, models must:
- Decompose complex reasoning arguments into elementary inference steps
- Classify each step as one of three Peircean reasoning paradigms:
  - **Deduction**: Deriving specific conclusions from general rules
  - **Induction**: Generalizing patterns from observations
  - **Abduction**: Forming hypotheses to explain phenomena
- Construct a Reasoning Logic Tree (RLT) that explicitly represents the logical structure

### 📊 ARCHE Bench Dataset

- **70 peer-reviewed articles** from *Nature Communications* (2025)
- **Balanced domains**: 35 Biological Sciences + 35 Physical Sciences
- **Rich context**: 2,164 introduction sentences, 1,891 citations, 38,000+ viewpoints
- **Real scientific reasoning**: Each article includes extracted viewpoints and reasoning chains

### 📐 Reasoning Logic Tree (RLT)

A structured graph representation where:
- **Nodes**: Scientific viewpoints with traceable sources
- **Edges**: Six fine-grained inference types
  - **Deduction-Rule (DR)** & **Deduction-Case (DC)**
  - **Induction-Common (ICo)** & **Induction-Case (ICa)**
  - **Abduction-Knowledge (AK)** & **Abduction-Phenomenon (AP)**
- **Structure**: Single-rooted directed acyclic graph (DAG)

### 📏 Evaluation Metrics

**Entity Coverage (EC)**: Measures how comprehensively the RLT captures core scientific concepts
- Proportion of key scientific entities present in valid reasoning steps
- Assesses content completeness

**Reasoning Edge Accuracy (REA)**: Evaluates logical validity of individual reasoning steps
- Three-model voting system (o3, Claude-Sonnet-4, Gemini-2.5-Pro)
- Validates format consistency and logical correctness
- Measures step-by-step reasoning quality

## Benchmark Results

We evaluated 10 state-of-the-art LLMs in zero-shot settings:

| Model | REA (↑) | EC (↑) |
|-------|---------|--------|
| Gemini-2.5-Pro (Thinking) | **41.4%** | 54.1% |
| Gemini-2.5-Pro | 39.5% | 56.7% |
| o3 | 35.6% | 60.5% |
| Grok-3 | 33.1% | 53.8% |
| Claude-Sonnet-4 (Thinking) | 28.8% | 53.1% |
| Doubao-Seed-1.6 (Thinking) | 28.2% | 55.3% |
| Claude-Opus-4 (Thinking) | 24.2% | **69.7%** |
| Grok-4 | 22.2% | 61.7% |
| DeepSeek-R1 | 20.1% | 28.7% |
| GPT-4o | 15.8% | 24.3% |

### Key Findings

- **Trade-off between precision and coverage**: Models achieving higher EC often sacrifice REA, and vice versa
- **Limited reasoning formalization**: Even top models struggle to exceed 50% accuracy in both metrics
- **Paradigm confusion**: Models systematically struggle to distinguish between reasoning types
- **Gap from human reasoning**: Current LLMs show fundamental limitations in structured, paradigm-grounded scientific reasoning

## Dataset Structure

```
arche/
├── datasets/
│   ├── articles/          # 70 Nature Communications papers
│   ├── viewpoints/        # Extracted viewpoints from papers and citations
│   └── metadata/          # Paper metadata and citation information
└── scripts/

```

## Getting Started

### Requirements

- Python 3.8+
- Access to LLM APIs (OpenAI, Anthropic, Google, etc.)
- Dependencies: `networkx`, `requests`, `pandas`


## Citation

If you use ARCHE in your research, please cite:

```bibtex
@inproceedings{arche2026,
  title={ARCHE: Latent Reasoning Chain Extraction for Evaluating Scientific Reasoning in Large Language Models},
  booktitle={Proceedings of the 40th AAAI Conference on Artificial Intelligence},
  year={2026}
}
```

## Dataset Statistics

| Metric | Value |
|--------|-------|
| Total Articles | 70 |
| Total Sentences | 2,164 |
| Total Viewpoints (Papers) | 5,418 |
| Total Citations | 1,891 |
| Total Viewpoints (Citations) | 33,321 |
| **Total Viewpoints** | **38,739** |
| Avg. Sentences per Article | 30.9 |
| Avg. Viewpoints per Article | 77.4 |
| Avg. Citations per Article | 27.0 |

## License

This dataset is released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). All articles are from *Nature Communications*, which are open-access and compatible with this license.



## Contact

For questions or issues, please open an issue on this repository or contact the authors.

