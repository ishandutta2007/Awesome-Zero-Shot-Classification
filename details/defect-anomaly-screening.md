# Zero-Shot Defect & Anomaly Screening in Manufacturing

**Zero-Shot Defect and Anomaly Screening** is a cutting-edge visual application of zero-shot classification (e.g., using frameworks like WinCLIP) for industrial quality control.

## Overview
In manufacturing lines, gathering anomalous data is notoriously difficult because defects (like hairline fractures, misaligned rivets, or paint chips) occur rarely and are highly diverse. Standard supervised models fail because they cannot anticipate every possible defect signature. Zero-shot visual models solve this by comparing image patches to textual descriptions of normal and defective states.

```mermaid
graph TD
    Image[Assembly Line Object Image] --> Encoder[Multi-Scale Visual Patch Encoder]
    Encoder --> Patches["Patch Feature Maps"]
    
    Prompts["Text Prompts:<br>- 'a perfect product surface'<br>- 'a surface with a hairline fracture'<br>- 'a surface with a misaligned joint'"] --> TextEncoder[Text Encoder]
    TextEncoder --> TextVectors[Semantic Class Vectors]
    
    Patches & TextVectors --> Matching[Cosine Similarity Alignment]
    Matching --> Map[Zero-Shot Anomaly Map]
    Map --> Decision["Anomaly Flagged (If similarity to defect > threshold)"]
```

## Key Frameworks: WinCLIP (CVPR 2023)
WinCLIP adapts CLIP for zero-shot anomaly detection by:
1. **Window-Based Multi-Scale Extraction:** Evaluating the image using overlapping windows/patches to localize spatial defects.
2. **Compositional Prompt Ensembling:** Creating a robust textual matrix describing normal states (e.g., `"flawless metal surface"`) and specific anomalies (e.g., `"scratched metal surface"`, `"dented metal surface"`).

[← Back to README](../README.md)
