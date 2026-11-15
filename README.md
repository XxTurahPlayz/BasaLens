# BasaLens 🌏

**Comparing AI Translation Performance Between Balinese and Indonesian**

## About the Project

BasaLens is an AI research prototype that evaluates how well Meta's NLLB-200 model translates English into two Indonesian regional and national languages: Balinese and Indonesian.

The project investigates whether translation performance differs between the two languages and whether beam search improves translation quality.

## Research Methodology

- **AI Model:** `facebook/nllb-200-distilled-600M`
- **Dataset:** FLORES+ (`devtest`)
- **Source Language:** English (`eng_Latn`)
- **Target Languages:** Indonesian (`ind_Latn`) and Balinese (`ban_Latn`)
- **Sample Size:** 100 aligned sentences
- **Decoding Methods:** Greedy Search and Beam Search (4 beams)
- **Evaluation Metric:** chrF

## Results

| Language | Greedy | Beam Search |
|---|---:|---:|
| Balinese | 46.81 | 46.41 |
| Indonesian | 69.06 | 69.53 |

The results show higher chrF scores for Indonesian in this sample. Beam search produced only small differences compared with greedy decoding.

## Human Review

A fluent Balinese speaker informally reviewed 25 Balinese translations. The feedback indicated that many translations needed improvement, some were considered clear and natural, and none were judged completely unusable.

## Interactive Demo

BasaLens includes a Gradio interface that allows users to enter English text and generate translations into Balinese or Indonesian.

## Limitations

- Evaluation uses only 100 benchmark sentences.
- chrF measures character-level similarity and does not fully evaluate meaning or naturalness.
- Balinese dialects and cultural context may affect translation quality.
- Human review was informal and involved one reviewer.
- This prototype is intended for research and educational purposes, not certified translation.

## Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- FLORES+
- SacreBLEU
- Gradio
- Google Colab

## Acknowledgements

This project uses Meta's NLLB-200 model and the FLORES+ dataset.

**Model license:** CC-BY-NC 4.0  
**Dataset license:** CC BY-SA 4.0

---

*BasaLens — Exploring AI Translation for Balinese.*
