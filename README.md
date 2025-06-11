# Large Language Models for Toxic Language Detection in Low-Resource Balkan Languages

This repository accompanies the paper:

**Large Language Models for Toxic Language Detection in Low-Resource Balkan Languages**  
Amel Muminovic, Amela Kadric Muminovic

## Overview

This repository provides resources and information related to our study on evaluating large language models (LLMs) for toxic language detection in Serbian, Croatian, and Bosnian.  
The work introduces a manually labeled dataset of 4,500 YouTube and TikTok comments and benchmarks four state-of-the-art LLMs (GPT-3.5 Turbo, GPT-4.1, Gemini 1.5 Pro, and Claude 3 Opus) in both zero-shot and context-augmented modes.

## Dataset Access

**The full dataset will be made publicly available in this repository upon acceptance of the paper.**

If you would like to access the dataset earlier for non-commercial research or to reproduce the results, please contact the first author:

- **Email:** [amcenp@gmail.com](mailto:amcenp@gmail.com)
- **LinkedIn:** [Amel Muminovic](https://www.linkedin.com/in/amel-muminovic-b5878173/)

Requests will be reviewed promptly. The dataset will be shared for academic, non-commercial use.

## Citation

If you use or reference this work, please cite the following:

```bibtex
@article{muminovic2025llmbalkan,
  title={Large Language Models for Toxic Language Detection in Low-Resource Balkan Languages},
  author={Muminovic, Amel and Kadric Muminovic, Amela},
  year={2025},
  note={Manuscript under review}
}
```


## Reproduction Guide

To help researchers reproduce our results, we provide a high-level outline of our experimental pipeline below. If you need further details or scripts, please contact the authors.

### 1. Data Collection
- Scrape YouTube and TikTok comments using the official YouTube Data API and a TikTok comment scraper.
- Select videos from politics, music, sports, and pop culture for each target language (Serbian, Croatian, Bosnian).

### 2. Annotation
- Manually label each comment as Toxic or Non-Toxic according to criteria in the paper.
- Use two annotators, resolve disagreements by consensus, and measure inter-annotator agreement.

### 3. Preprocessing
- Exclude comments not in the target languages.
- Clean and anonymize data (remove IDs, preserve context).
- Manually craft a short context snippet for each video.

### 4. Model Inference

**Prompt for Zero-Shot:**
Analyze the following comment written in Serbian, Bosnian, or Croatian. The comment is a response to a YouTube or TikTok video. 
Determine if the comment contains toxic language, including insults, hate speech, threats, harassment, or harmful sarcasm. Consider regional slang, sarcasm, tone, and cultural context. Respond with 0 if the comment is not toxic, and 1 if it is toxic. Do not respond with any other text. Comment is: <COMMENT_TEXT>

markdown
Copy

**Prompt for Context-Augmented:**
Analyze the following comment written in Serbian, Bosnian, or Croatian. The comment is a response to a YouTube or TikTok video. Use the provided context to understand what the video is about. Context about video: <CONTEXT>
Determine if the comment contains toxic language, including insults, hate speech, threats, harassment, or harmful sarcasm. Consider regional slang, sarcasm, tone, and cultural context. Respond with 0 if the comment is not toxic, and 1 if it is toxic. Do not respond with any other text. Comment is: <COMMENT_TEXT>

vbnet
Copy

- Send each comment (with or without context) to the model API with temperature=0.

### 5. Evaluation
- Calculate accuracy, precision, recall, F1, and false positive rate for each model and setup.
- Compare results across languages and models.

If you require example code or have questions, please contact the first author at [amcenp@gmail.com](mailto:amcenp@gmail.com).

---

**Tip:**  
If/when you decide to share the actual code, just add a `/scripts` folder and update the README with usage instructions.

**Including pseudocode or a workflow is much better than nothing**—it signals transparency, helps reviewers, and makes it easier for others to reproduce your work.

Let me know if you want to include a LaTeX algorithm block as well!
