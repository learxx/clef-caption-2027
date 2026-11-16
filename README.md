# ImageCLEFmedical Caption 2027

Supplementary material for the **ImageCLEFmedical Caption 2027** task, the 11th edition of the task at [CLEF 2027](https://clef2027.clef-initiative.eu/) in Bucharest.

The repository contains examples and evaluation and submission scripts for each subtask. Use the official task website for the full task description, the schedule, and dataset access.

> 🌐 **Task website:** https://www.imageclef.org/2027/medical/caption
> 📝 **Registration:** [ImageCLEF 2027 registration instructions](https://www.imageclef.org/2027)

---

## About the task

Interpreting and summarizing medical images such as radiology scans takes a lot of time and needs highly trained experts. This step is often a bottleneck in clinical diagnosis. This task asks for automatic methods that map visual information to short textual descriptions.

The data comes from **[ROCOv2](https://doi.org/10.48550/ARXIV.2405.10004)** (Radiology Objects in COntext version 2), a large collection of figures from open-access biomedical articles in PubMed Central. The images come with UMLS concepts extracted from their original captions. This year, a **synthetic dataset** is provided alongside the original data.

## Subtasks

| # | Subtask | Goal | Evaluation |
|---|---------|------|------------|
| 1 | **Concept Detection** | Identify the UMLS concepts present in a medical image | Set coverage metrics (precision, recall, F1, …) |
| 2 | **Caption Prediction** | Write a coherent caption for the whole image | BERTScore (primary), ROUGE (secondary), plus MedBERTScore, MedBLEURT, BLEU |
| 3 | **Caption Error Classification** 🆕 | Classify a caption as correct, or name its error types (e.g. wrong anatomy, missing findings, added findings) | Set coverage metrics (precision, recall, F1, …) |
| + | **Explainable Task** | Explain your system's output for any of the subtasks above | Manual rating by a radiologist and a VLM-as-a-judge |

For Concept Detection and Caption Prediction, participants can train on the original dataset, the synthetic dataset, or both. The test sets contain both original and synthetic data. Caption Error Classification uses images with synthetic captions.

## Repository structure

```
.
├── concept_detection/              # Subtask 1: evaluation & submission scripts
├── caption_prediction/             # Subtask 2: evaluation & submission scripts
├── caption_error_classification/   # Subtask 3: evaluation & submission scripts
├── explainability/                 # Explainable task: example explanations & submission guidelines
└── README.md
```

Each subfolder has its own README with details on input/output formats, how to run the evaluation locally, and how to validate a submission file.

## Baselines

Trained baselines are provided for reference:

- **Concept Detection:** EfficientNet-based model
- **Caption Prediction:** Qwen3-4B-VL, fine-tuned with Unsloth

## Working notes

- **Image attribution:** If you include dataset images in your paper, put the attribution string in the figure caption or directly next to the image. A lookup file mapping image IDs to attributions will be linked here.
- **Citations:** Cite the ImageCLEF 2027 overview paper, the ImageCLEFmedical Caption 2027 task overview paper, and the ROCOv2 dataset paper (see [Citation](#citation)).
- **Reproducibility:** We encourage you to release code, trained models, and instructions in a public repository and link to it in your paper.
- **Preprints:** Before citing an arXiv preprint, check whether it has been published in the meantime, for example with [preprintresolver.eu](https://preprintresolver.eu/).

Teams that submit working notes and the best-ranked teams per subtask get a **certificate**.

## Citation

BibTeX for the 2027 overview papers will be added once they are available. Please cite the dataset paper:

```bibtex
@misc{ruckert2024rocov2,
  title     = {{ROCOv2}: Radiology Objects in {COntext} Version 2, an Updated Multimodal Image Dataset},
  author    = {R{\"u}ckert, Johannes and Bloch, Louise and Br{\"u}ngel, Raphael and Idrissi-Yaghir, Ahmad and Sch{\"a}fer, Henning and Schmidt, Cynthia S. and Koitka, Sven and Pelka, Obioma and Ben Abacha, Asma and Garc{\'i}a Seco de Herrera, Alba and M{\"u}ller, Henning and Horn, Peter A. and Nensa, Felix and Friedrich, Christoph M.},
  year      = {2024},
  doi       = {10.48550/ARXIV.2405.10004}
}
```

## Organizers

- Benjamin Bracke, Lea Reinartz, Christoph M. Friedrich, Hendrik Damm, Momodou B. Jallow, Jakub Szczelina, Raphael Brüngel: *University of Applied Sciences and Arts Dortmund, Germany*
- Asma Ben Abacha: *Microsoft, USA*
- Alba García Seco de Herrera: *University of Essex, UK*
- Henning Müller: *University of Applied Sciences Western Switzerland, Sierre, Switzerland*
- Tabea M. G. Pakull, Henning Schäfer: *Institute for Transfusion Medicine, University Hospital Essen, Germany*
- Cynthia S. Schmidt: *Institute for Artificial Intelligence in Medicine (IKIM), University Hospital Essen, Germany*
- Anna Chatzipapadopoulou: *Athens University of Economics and Business, Greece*

For questions, open an issue in this repository or contact the organizers (contact details are on the task website).

## Acknowledgments

The images come from the open-access subset of [PubMed Central](http://www.ncbi.nlm.nih.gov/pmc/).
