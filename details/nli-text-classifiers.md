# NLI-Based Zero-Shot Classifiers (Text-Only)

**NLI-Based Zero-Shot Classifiers** are specialized language models trained on Natural Language Inference datasets to categorize text by calculating logical entailment.

## Overview
These models take two inputs: a premise (the text to classify) and a hypothesis (representing a potential category). They run the inputs through a cross-attention layer to evaluate their semantic and logical alignment.

```mermaid
graph TD
    Premise[Premise Text] --> Tokenizer
    Hypothesis[Hypothesis: 'This is about {label}'] --> Tokenizer
    Tokenizer --> Input["[CLS] Premise [SEP] Hypothesis [SEP]"]
    Input --> Transformer[Transformer Model e.g. BART, DeBERTa]
    Transformer --> ClassHead[Classification Head]
    ClassHead --> Logits["Entailment / Contradiction Logits"]
    Logits --> Score[Entailment Probability Score]
```

## Popular Architectures
- **BART-Large-MNLI:** An encoder-decoder architecture fine-tuned on the Multi-Genre Natural Language Inference dataset. Excellent baseline for general-purpose zero-shot categorization.
- **DeBERTa-v3-Large-XNLI:** Features disentangled attention and improved training setups. Offers higher accuracy and robust reasoning capabilities for cross-lingual zero-shot classification.

## Implementation Workflow
To categorize a sentence like `"Stocks fell today."` among classes `["finance", "sports", "politics"]`:
1. Generate hypotheses:
   - `"This text is about finance."`
   - `"This text is about sports."`
   - `"This text is about politics."`
2. Feed each pair to the NLI classifier.
3. Apply Softmax to the entailment scores of the three candidate hypotheses to select the class.

[← Back to README](../README.md)
