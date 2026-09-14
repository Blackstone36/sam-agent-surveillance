 # SAM-Agent: Explainable Velocity-Aware Surveillance

[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/downloads/)
[![PyTorch 2.3.1](https://img.shields.io/badge/PyTorch-2.3.1-red.svg)](https://pytorch.org/)
 

## Overview

Modern surveillance systems generate large volumes of video data, but conventional computer-vision models often focus primarily on visual perception without providing sufficient behavioral interpretation or actionable explanations.

**SAM-Agent** is an agentic surveillance framework that bridges the gap between pixel-level perception and intelligent security reasoning. The system integrates **Segment Anything Model 2.1 (SAM 2.1)** with Kalman-filtered motion analysis, explainable AI, and deterministic incident reporting.

Rather than only segmenting and tracking objects, SAM-Agent analyzes movement patterns, identifies potential anomalies, explains its decisions, and produces structured operator-facing reports.

## Key Features

- **Perception Layer:** Zero-shot spatio-temporal mask propagation using SAM 2.1 Hiera-Tiny.
- **Reasoning Layer:** Kalman-filtered kinematic analysis using velocity, acceleration, grid variance, and dynamic 3-sigma thresholds.
- **Explainability Layer:** Transformer attention rollout with a quantitative **Focus Ratio** metric for evaluating attention alignment.
- **Communication Layer:** Deterministic, template-based natural-language incident reporting designed to minimize hallucination.
- **Modular Architecture:** Separate perception, reasoning, explainability, and communication components for easier experimentation and extension.

## Reported Performance

SAM-Agent was evaluated on the **Intel People Detection** and **UCSD Ped2** benchmarks.

| Metric | Intel People Detection | UCSD Ped2 |
|---|---:|---:|
| **F1-Score** | **0.9000** | **0.852** |
| **Precision** | 0.9000 | 0.924 |
| **Recall** | 0.9000 | 0.803 |
| **False Alarm Rate** | 0.53% | 4.88% |
| **AUC / AP** | — | 0.718 / 0.911 |

### System Efficiency

- **Kinematic jitter reduction:** 70.85% through Kalman state estimation.
- **Processing speed:** 2.28 iterations/second on an NVIDIA Tesla T4.
- **Mean XAI Focus Ratio:** 0.89.
- **Test GPU:** NVIDIA Tesla T4 with 16 GB VRAM.

> The reported metrics reflect the experiments documented for this project. For reproducibility, dataset splits, evaluation protocols, configuration files, and experiment logs should be included with the research implementation.

## System Architecture

SAM-Agent is organized into four functional layers:

1. **Perception**
   - Ingests video streams.
   - Generates binary object masks and confidence scores using SAM 2.1.

2. **Reasoning**
   - Extracts object centroids and motion features.
   - Applies Kalman filtering to reduce tracking noise.
   - Computes multivariate motion statistics for anomaly detection.

3. **Explainability**
   - Extracts Transformer attention information.
   - Produces saliency visualizations.
   - Calculates the Focus Ratio to quantify attention alignment.

4. **Communication**
   - Converts verified metadata into deterministic natural-language templates.
   - Produces structured reports for surveillance operators.

For the complete mathematical formulation and Algorithm 1 pseudocode, refer to the associated research paper.

## Technology Stack

- Python 3.10+
- PyTorch 2.3.1
- Segment Anything Model 2.1
- Kalman Filtering
- Computer Vision
- Explainable AI
- Video Anomaly Detection
- Deterministic Natural-Language Reporting

## Installation

### Prerequisites

- Python 3.10 or newer
- NVIDIA GPU with approximately 12 GB or more VRAM recommended
- CUDA-compatible PyTorch installation
- Git

The project was tested on an NVIDIA Tesla T4 with 16 GB VRAM.

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/sam-agent-surveillance.git
cd sam-agent-surveillance
```

### 2. Create and Activate a Virtual Environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Install SAM 2.1

Follow the official SAM 2 installation instructions:

```bash
pip install git+https://github.com/facebookresearch/sam2.git
```

## Project Structure

```text
sam-agent-surveillance/
├── README.md
├── requirements.txt
├── LICENSE
├── configs/
├── data/
├── models/
├── notebooks/
├── src/
├── results/
└── experiments/
```

> Update this structure to match the actual files and folders in your repository before publishing.

## Reproducibility

To make the research implementation easier to reproduce, consider including:

- Dataset preparation instructions.
- Model checkpoints or download instructions.
- Configuration files.
- Evaluation scripts.
- Experiment logs.
- Generated visualizations.
- Hardware and software specifications.

## Research Contributions

The project combines:

1. SAM 2.1-based video perception.
2. Kalman-filtered velocity-aware reasoning.
3. Quantitative attention-based explainability.
4. Deterministic incident report generation.

This combination is intended to support more interpretable and operationally useful surveillance anomaly detection.

## Acknowledgements

This project builds upon the research and open-source contributions of the Segment Anything Model 2 project and the broader computer-vision and explainable-AI communities.

## Author

**Hafsa Rehman**

 
