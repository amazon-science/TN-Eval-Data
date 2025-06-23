# TN-Eval-Data

This repository contains data for the [TN-Eval](https://github.com/amazon-science/TN-Eval) project.

We use 50 conversations from the [AnnoMI](https://github.com/uccollab/AnnoMI) dataset and collect corresponding notes and evaluations.

For each conversation, the following note versions are included:
- Human-written notes
- Llama 3.1 70B generated notes
- Mistral Large V2 generated notes

Each note is evaluated by:
- 2 human annotators
- Llama 3.1 70B
- Mistral Large V2

## Data Format
Each entry in the dataset is structured as follows:
```
{
  "id": "0",                      // Conversation ID
  "mi_quality": "high",           // AnnoMI dataset split (only high-quality used)
  "human": {                      // Human-written note and evaluations
    "note": { ... },              // SOAP-style clinical note
    "metrics_llama31_70B": { ... },       // Automatic evaluation by Llama 3.1
    "metrics_mistral_large_v2": { ... },  // Automatic evaluation by Mistral
    "align_score": { ... },               // AlignScore metric
    "metrics_human": { ... }              // Human evaluation (2 annotators)
  },
  "llm_llama31_70B": { ... },     // Llama 3.1 generated note and evaluations
  "llm_mistral_large_v2": { ... } // Mistral Large V2 generated note and evaluations
}
```

Evaluations are conducted per note section. For both human and automatic evaluations, the structure is consistent. Below is an example for the subjective section:
```
"subjective": {
  "rubric_completeness_raw": { ... }, // Raw rubric scores (completeness)
  "rubric_conciseness_raw": { ... },  // Raw rubric scores (conciseness)
  "likert_completeness": 2,           // Likert-scale score for completeness
  "likert_conciseness": 4,            // Likert-scale score for conciseness
  "likert_faithfulness": 5,           // Likert-scale score for faithfulness
  "rubric_completeness": 0.33,        // Aggregated rubric completeness score
  "rubric_conciseness": 0.89          // Aggregated rubric conciseness score
}
```

## Conversation Data
Please refer to https://github.com/uccollab/AnnoMI for the conversation transcripts.


## Citation
If you use our data, please cite
```
@inproceedings{shah2025tneval,
  title={TN-Eval: Rubric and Evaluation Protocols for Measuring the Quality of Behavioral Therapy Notes},
  author={Shah, Raj Sanjay and Xu, Lei and Liu, Qianchu and Burnsky, Jon and Bertagnolli, Drew and Shivade, Chaitanya},
  booktitle={Proceedings of the 63nd Annual Meeting of the Association for Computational Linguistics: Industry Track},
  year={2025}
}
```
