# BasaLens 🌏

### Evaluating AI Translation Quality for Balinese and Indonesian

**BasaLens** is an AI research prototype that investigates how reliably Meta's NLLB-200 model translates English into Balinese and Indonesian.

Rather than simply generating translations, BasaLens evaluates translation quality through automatic metrics, language identification, decoding comparisons, and human assessment.

## 🎯 Research Objectives

- Compare English-to-Balinese and English-to-Indonesian translation performance.
- Investigate whether beam search improves translation quality.
- Examine language consistency in generated Balinese translations.
- Evaluate translation quality in practical Banjar announcement scenarios.

## 🧠 Model and Technologies

| Component | Technology |
|---|---|
| Translation Model | `facebook/nllb-200-distilled-600M` |
| Programming Language | Python |
| Deep Learning | PyTorch |
| Model Framework | Hugging Face Transformers |
| Benchmark Dataset | FLORES+ |
| Evaluation Metric | chrF (SacreBLEU) |
| Language Identification | XLM-RoBERTa-based classifier |
| Interactive Demo | Gradio |
| Development Environment | Google Colab |

## 🔬 Research Methodology

### 1. FLORES+ Benchmark Evaluation

- Dataset: FLORES+ (`devtest`)
- Language pairs: English → Balinese and English → Indonesian
- Evaluation sample: 100 aligned sentences
- Random seed: 42
- Decoding strategies: Greedy Search and Beam Search (4 beams)
- Metric: chrF

### 2. Language Identification

A multilingual language identification model was used to examine the language distribution of generated Balinese translations.

The classifier was validated using 100 Balinese and 100 Indonesian reference sentences.

### 3. Real-World Banjar Evaluation

A separate evaluation was conducted using 25 original English announcements designed around community communication scenarios.

The translations were compared against human-provided Balinese references and assessed by one fluent Balinese speaker.

Evaluation criteria:
- Meaning preservation
- Fluency
- Language consistency
- Suitability for community announcements

### 4. Decoding Strategy Experiment

Beam Search with 4 and 8 beams was compared on the same 25 Banjar announcements.

A bootstrap analysis with 2,000 iterations was used to estimate uncertainty in the chrF score difference.

## 📊 Key Results

### FLORES+ Benchmark Results

| Language | Greedy | Beam 4 |
|---|---:|---:|
| Balinese | 46.81 | 46.41 |
| Indonesian | 69.06 | 69.53 |

Indonesian achieved higher chrF scores than Balinese in this evaluation sample.

### Language Identification Results

- Validation accuracy: **92.5%**
- Generated Balinese outputs classified as Balinese: **93%**
- Classified as Javanese: **5%**
- Classified as Sundanese: **2%**

These predictions are indicative rather than definitive because the classifier did not achieve perfect validation accuracy.

### Banjar Announcement Evaluation

| Evaluation | Result |
|---|---:|
| Number of announcements | 25 |
| Beam 4 chrF | 41.01 |
| Human meaning score | 2.76/5 |
| Human fluency score | 2.16/5 |
| Language consistency score | 2.64/5 |
| Overall human evaluation | 2.52/5 |
| Usable after editing | 9/25 |
| Not suitable as-is | 16/25 |

The human evaluation revealed weaknesses in semantic accuracy, grammatical fluency, vocabulary, and language consistency.

### Beam Search Comparison

| Configuration | chrF |
|---|---:|
| Beam 4 | 41.01 |
| Beam 8 | 40.77 |

- Score difference (Beam 8 − Beam 4): **−0.24**
- 19 out of 25 outputs were identical.
- Bootstrap 95% confidence interval: **[−1.00, 0.30]**

The confidence interval includes zero, so the experiment does not establish a reliable advantage for either decoding configuration.

## ⚠️ Limitations

- The benchmark experiment used a sample of 100 sentences.
- The Banjar evaluation involved only 25 custom announcements.
- Human evaluation involved one fluent Balinese speaker.
- Human references may contain regional, stylistic, or Indonesian-influenced expressions.
- chrF measures character-level similarity and cannot fully assess meaning, naturalness, or cultural appropriateness.
- The language identification classifier is imperfect.
- Results should not be generalized to every Balinese dialect or communication context.

## 🚧 Experimental Refinement

An initial refinement experiment was attempted using `google/mt5-small`.

The model returned a special sentinel token instead of a corrected Balinese translation. It was therefore excluded from further performance evaluation.

No translation improvement from this model is claimed.

## 💡 Conclusion

NLLB-200 can generate Balinese translations, but the experiments indicate that its output quality remains inconsistent.

The gap between automatic evaluation and human assessment highlights why low-resource language translation should not be evaluated using a single metric.

BasaLens demonstrates a research-oriented approach to examining translation quality, identifying weaknesses, and encouraging further development of Balinese language technology.

**BasaLens is a research prototype, not a certified translation system.**

## 📁 Repository Contents

| File | Description |
|---|---|
| `BasaLens_Hackathon.ipynb` | Complete research notebook and experiments |
| `BasaLens_Final_Banjar_Evaluation.csv` | Sentence-level Banjar evaluation data |
| `basalens_aggregate_scores.csv` | Aggregate benchmark results |
| `basalens_translation_quality_100_examples.png` | Translation quality comparison chart |
| `requirements.txt` | Python dependencies |

## 📜 Acknowledgements

This project uses Meta's NLLB-200 multilingual translation model and the FLORES+ dataset.

- NLLB-200 model license: CC-BY-NC 4.0
- FLORES+ dataset license: CC BY-SA 4.0

---

**BasaLens — Making Balinese Translation Quality Measurable.**
