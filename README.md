# Zero-Shot Industrial Defect Segmentation

Overview
Developed a zero-shot defect segmentation framework for industrial inspection tasks using Segment Anything Model (SAM) integrated with Vision Transformer (ViT) fine-tuning. The pipeline achieved a 38% IoU improvement over baseline unsupervised methods, demonstrating effective segmentation with minimal labeled supervision on the MVTec AD dataset.

Framework
Domains: Deep Learning, Computer Vision
Frameworks/Tools: SAM, ViT Fine-Tuning, PyTorch
Goal: Segment industrial defects without extensive labeled data
Affiliation: National University of Sciences and Technology (NUST)

Scope
 Designed a zero-shot segmentation pipeline for defect localization in industrial imagery.
 Leveraged SAM’s universal segmentation priors to generalize across unseen defect types.
 Fine-tuned ViT encoders using few-shot exemplars to adapt embeddings to industrial textures.
 Integrated prompt-based inference to segment fine-grained regions without retraining.

 Methodology
 1. Base Architecture

 Utilized SAM’s encoder-decoder segmentation backbone for zero-shot region detection.
 Adapted ViT features for industrial texture embeddings through lightweight fine-tuning.

 2. Prompt-Guided Refinement

 Incorporated box, point, and text prompts to guide defect region predictions dynamically.
 Applied feature alignment losses to adapt SAM embeddings to industrial domains.

 3. Evaluation Strategy

 Conducted tests on MVTec AD dataset across metal, fabric, and PCB defect categories.
 Compared against U-Net, DeepLabV3+, and DINO-based few-shot baselines.

Results
| Metric            | Baseline (U-Net) | Proposed (SAM + ViT) | Improvement |
| IoU               | 41%              | 79%              | +38%        |
| F1 Score          | 0.62             | 0.88             | +26%        |
| Label Requirement | 100%             | <10%             | -90%        |

Key Outcomes:
 Achieved robust zero-shot segmentation performance with minimal data.
 Enabled fine-grained defect localization across diverse materials.
 Reduced reliance on manual annotation by over 90%.

System Workflow (Textual Diagram)

┌────────────────────────┐
│  Industrial Image Input │
└────────────┬───────────┘
             │
   ┌─────────▼───────────┐
   │  SAM Encoder         │
   │  (Promptable Model)  │
   └─────────┬───────────┘
             │
   ┌─────────▼───────────┐
   │  ViT Fine-tuning     │
   │  (Feature Alignment) │
   └─────────┬───────────┘
             │
   ┌─────────▼───────────┐
   │  Segmentation Head   │
   │  (Defect Mask Output)│
   └──────────────────────┘


Conclusion
This project validated SAM + ViT integration as a scalable zero-shot segmentation strategy for industrial defect inspection. It effectively bridged the gap between general-purpose segmentation and domain-specific adaptation, making it suitable for data-scarce manufacturing environments.

Future Work
 Integrate CLIP-based visual-text alignment for defect-type understanding.
 Extend to 3D industrial scans using SAM-3D or multimodal visual encoders.
 Deploy as a lightweight edge AI system for real-time defect segmentation.

Closest Research Alignment
> Kirillov, A. et al. (2023). Segment Anything. arXiv preprint arXiv:2304.02643.
> This project extends SAM’s zero-shot generalization into industrial inspection contexts, reinforcing the value of promptable segmentation models under low-data regimes.
