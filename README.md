# LIKE

## Introduction

In the past decade, there has been rapid growth in fake news and spread of misinformation. This has become even worse during COVID-19 pandemic.

This surge of misleading information, i.e. "infodemic", has profound consequences impacting adherence to pandemic-appropriate behavior. So there is a need to detect fake news in an accurate manner.

In today's Twitterverse, a deluge of fake news is generated continuously, posing a formidable challenge to state-of-the-art detectors. These detectors face knowledge obsolescence, for example, models trained in 2022 are inadequate for handling novel data in 2024. Moreover, retraining these detectors on newer data also leads to catastrophic forgetting due to shift in model weights.

To address these challenges, Argus was proposed in this [paper](https://asuprem.com/static/content/koinitial.pdf) which detects novel data using Lipschitz smoothness enabling dynamic adaptation of detection models to evolving misinformation trends.

This repository extends research based on Argus in developing state-of-the-art detectors.

LIKE stands for LIve Knowledge Evolution and it aims to explore the problem of knowledge obsolesence including ways to mitigate it.

## Our High-Level Approach
We generate Fake News Covid (FNC) dataset by scraping tweets from Twitter and filering out tweets containing information related to COVID.

This dataset is spanned over multiple months.

We then manually label few data points as fake or not fake, and train expert models to synthetically label the entire dataset based on our labeled data points.

And then we train our fake news detectors for each month from the labeled datasets corresponding to that month.

> For more details on training expert models to synthetically label the dataset, please check this notebook: [Semantic_Masking.ipynb](src/Fakeddit/Semantic_Masking.ipynb).

> For more details on creating dataset and training fake news detector, please check this notebook: [Fake_News_Labeler_v3.ipynb](src/FNC/Fake_News_Labeler_v3.ipynb).

We use [EdnaML](https://arxiv.org/abs/2211.06783) framework in above notebooks to ease efforts involved in setting up model training and data processing pipelines.

## Acknowledgements

This repository was originally created from [EdnaML](https://github.com/asuprem/EdnaML) developed by Abhijit Suprem and Professor Calton Pu.

## References
1. Evaluating Generalizability of Fine-Tuned Models for Fake News Detection; Abhijit A Suprem and Calton Pu ([paper](https://arxiv.org/abs/2205.07154))
2. EdnaML: A Declarative API and Framework for Reproducible Deep Learning; Abhijit A Suprem et al. ([paper](https://arxiv.org/abs/2211.06783))
3. The New-Normal of Fake News: Enhanced and Sustainable Multi-Expert Detection through Timely Adaptation to Counter Knowledge Obsolescence; Abhijit A Suprem and Calton Pu ([paper](https://asuprem.com/static/content/koinitial.pdf))
4. EdnaML Repository: [GitHub link](https://github.com/asuprem/EdnaML)