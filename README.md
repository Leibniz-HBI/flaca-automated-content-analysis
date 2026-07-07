# FLACA Automated Content Analysis Tutorials

This repository contains a collection of Python notebooks developed as an outcome of the consortium project **Few-Shot Learning for Automatic Content Analysis in Communication Studies (FLACA)**.

FLACA makes recent advances in Natural Language Processing accessible for automatic content analysis in communication science. The project focuses especially on few-shot text classification with pre-trained transformer language models, prompting and using large language models, and argument mining methods for coding semantically complex content categories with comparatively little annotated training data.

The tutorials in this collection provide practical e-learning resources for communication scientists who want to apply, evaluate, and further develop these methods in their own research. They cover workflows for automated content analysis, including fine-tuning smaller language models and prompting larger models, and are connected to FLACA's broader aim of strengthening data competencies for young academics through case studies, best practices, software, publications, and methods workshops.

## Best Practice Manual

Based on works and findings from FLACA, we compiled a comprehensive collection of best practices to approach automated content analysis:
[FLACA Best Practice Manual](https://leibniz-hbi.github.io/flaca-automated-content-analysis/)

## Tutorial Overview

The course consists of six tutorials that build from basic programming skills to applied automated content analysis workflows:

1. [Introduction to Python](<1_Introduction to Python.ipynb>) introduces Python syntax, data types, control structures, functions, modules, file handling, and working with tabular data in pandas.
2. [Text Classification Intro](<2_Text classification Intro.ipynb>) introduces supervised text classification with Flair NLP, including pretrained models, transformer-based classifier training, model evaluation, and prediction on unseen data.
3. [Zero-Shot Text Classification](<3_Zero-shot text classification.ipynb>) covers multilingual zero-shot classification for content analysis tasks, using offensive language detection as a practical example and discussing suitable and problematic category types.
4. [Domain Adaptation](<4_Domain adaptation.ipynb>) demonstrates how models can be adapted to target-domain data, including annotation of target data, intermediate fine-tuning, and intercoder agreement.
5. [LLM Prompting](<5_LLM-prompting.ipynb>) introduces prompting large language models for text classification, including basic prompt design, German tweet classification, quantization, and chat templates.
6. [Final Prediction and Analysis](<6_Final prediction and analysis.ipynb>) brings the workflow together through final model prediction, descriptive analysis, and interpretation of observed patterns.

FLACA was carried out in cooperation with the Leibniz-Institute for Media Research | Hans-Bredow-Institut and the University of Hamburg. The project was funded through the research plan **Data Action** of the Federal Ministry of Research, Technology and Space as part of the funding measure **Strengthening the Data Competences of Young Scientists**, financed through the EU recovery plan **NextGenerationEU**.

## Project Team

- University of Hamburg: Prof. Dr. Katharina Kleinen-von K&ouml;nigsl&ouml;w, Laura Liebig, Dr. Gerret von Nordheim, Dr.Kostiantyn Yanchenko
- Leibniz Institute for Media Research | Hans-Bredow-Institut: Dr. Gregor Wiedemann, Dr. Jonas Rieger, Mattes Ruckdeschel

## Project Information

- Duration: 2022-2025
- Project lead: Prof. Dr. Katharina Kleinen-von K&ouml;nigsl&ouml;w
- Sponsor: BMFTR
