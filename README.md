# Peptide and Protein Sequencing by Multinomial Diffusion Model

A comparative analysis of four state of the de novo peptide sequencing tools for wastewater proteomics applications.

## Project Overview

This project benchmarks four AI based de novo peptide sequencing tools spanning the evolution of the field from classical machine learning to modern diffusion based refinement. The goal is to identify which tool best supports environmental proteomics applications, particularly wastewater monitoring.

## Tools Compared

| Tool | Type | Year |
|------|------|------|
| Novor | Classical Machine Learning | 2015 | 
| Casanovo | Transformer Architecture | 2022 | 
| InstaNovo | Transformer + Beam Search | 2025 | 
| InstaNovo+ | Diffusion Based Refinement | 2025 | 

## Final Results

### E.coli Dataset (Validation - 21,805 spectra)

| Tool | AA Precision | AA Recall | Peptide Accuracy |
|------|--------------|-----------|------------------|
| Casanovo | **5.44%** | 5.33% | 0.00% |
| Novor | 4.78% | 4.71% | 0.00% |
| InstaNovo | 4.71% | 4.96% | 0.00% |
| InstaNovo+ | 5.07% | **5.24%** | 0.00% |

### Wastewater Dataset (Test - 61,150 spectra)

| Tool | Avg Confidence | Estimated FDR |
|------|---------------|---------------|
| Casanovo | N/A | 66.00% |
| Novor | N/A | 55.52% |
| InstaNovo | -6.58 | 59.72% |
| InstaNovo+ | **-0.52** | **18.65%** |

### Processing Time (NVIDIA A100 GPU)

| Tool | Total Time |
|------|-----------|
| Novor | 5.2 minutes |
| Casanovo | 19.3 minutes |
| InstaNovo | 81.4 minutes |
| InstaNovo+ | 150.2 minutes |

## Key Finding

**InstaNovo+ achieves a 41% FDR reduction** on wastewater samples compared to InstaNovo alone (from 59.72% down to 18.65%) validating the diffusion based refinement approach as a paradigm shift for de novo peptide sequencing.

## Project Report

[Download Complete Project Report (PDF)](./Project_Report.pdf)

## Implementation Details

### Dataset
- E.coli samples: 2 mzML files (21,805 spectra)
- Wastewater samples: 4 mzML files (61,150 spectra)
- Ground truth: MaxQuant database search results (3,162 peptides)
- Data provided by Dr. Yinyin Ye's Lab at University at Buffalo

### Environment
- Platform: Google Colab
- GPU: NVIDIA A100 (40 GB)
- Framework: PyTorch 2.5.0, CUDA 12.1
- Python: 3.12

### Evaluation Metrics
- Amino Acid Precision and Recall
- Peptide Level Accuracy
- False Discovery Rate (FDR) Estimation

## Author

- **Nabil Ahmad Khan**
- Department of Computer Science and Engineering
- University at Buffalo
- Email: nkhan23@buffalo.edu

## Key References

1. Eloff, K., et al. (2025) InstaNovo enables diffusion powered de novo peptide sequencing. *Nature Machine Intelligence*.
2. Yilmaz, M., et al. (2022) De novo mass spectrometry peptide sequencing with a transformer model. *ICML*.
3. Ma, B. (2015) Novor: Real Time Peptide de Novo Sequencing Software. *JASMS*.
