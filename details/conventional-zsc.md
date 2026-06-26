# Conventional Zero-Shot Classification

**Conventional Zero-Shot Classification** represents the classical evaluation setup in zero-shot learning frameworks, designed as a closed-world testing paradigm.

## Definition
In Conventional ZSC, the target dataset classes are divided into two completely disjoint sets:
1. **Seen Classes ($S$):** Categories for which labeled training instances are available.
2. **Unseen Classes ($U$):** Categories for which no training data exists.

During the test/inference phase, the evaluation is conducted under the strict assumption that the incoming data points belong **exclusively** to the unseen set ($U$).

```mermaid
graph TD
    subgraph Training Phase
        SeenData[Seen Class Data] --> Train[Train Attribute/Semantic Model]
    end
    
    subgraph Testing Phase (Conventional ZSC)
        TestData[Unseen Class Data] --> Predict[Model Inference]
        Predict --> Output["Output Search Space: Unseen Classes ONLY (U)"]
    end
```

## Key Characteristics
- **Simplified Search Space:** The classifier does not need to balance seen vs. unseen classes. It is guaranteed that the test sample is one of the unseen target classes.
- **Evaluation Utility:** Ideal for checking a model's basic ability to transfer knowledge to new domains via intermediate semantic representations (attributes or text embeddings).
- **Limitation:** Unrealistic for live production engineering. In real-world systems, incoming data can belong to either seen or unseen categories.

[← Back to README](../README.md)
