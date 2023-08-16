# gpt-llm-trainer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_) [![Open Main Version In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1mV9sAY4QBKLmS58dpFGHgwCXQKRASR31?usp=sharing)

## Overview

Training models is hard. You have to collect a dataset, clean it, get it in the right format, select a model, write the training code and train it. And that's the best-case scenario.

The goal of this project is to explore an experimental new pipeline to train a high-performing task-specific model. We try to abstract away all the complexity, so it's as easy as possible to go from idea -> performant fully-trained model.

**Simply input a description of your task, and the system will generate a dataset from scratch, parse it into the right format, and fine-tune a LLaMA 2 model for you.**

### Project Extensions

In this fork, we have extended the original project to address some critical challenges that are commonly encountered in machine learning processes. These include overfitting, ignoring minority classes, and amplification of biases. The added code and modifications are designed to deal with these issues in the following ways:

- **Overfitting Prevention**: By introducing techniques such as data augmentation and regularization, we strive to create a more generalized model that performs well on unseen data.

- **Minority Class Handling**: The class balancing logic ensures that minority classes are not overlooked, providing a fair representation and thus enhancing the model's predictive accuracy across all classes.

- **Bias Evaluation and Mitigation**: The extension includes a comprehensive bias evaluation and adjustment logic. It allows us to assess and minimize biases that might emerge from the data or model, ensuring that the predictions are fair and unbiased.

These enhancements align with best practices in machine learning and make the model more robust, accurate, and fair. Feel free to explore the updated code to understand how these additions work in detail.


## Features

- **Dataset Generation**: Using GPT-4, `gpt-llm-trainer` will generate a variety of prompts and responses based on the provided use-case.

- **System Message Generation**: `gpt-llm-trainer` will generate an effective system prompt for your model.

- **Fine-Tuning**: After your dataset has been generated, the system will automatically split it into training and validation sets, fine-tune a model for you, and get it ready for inference.

## Setup
1. [Open the notebook in Google Colab](https://colab.research.google.com/drive/1mV9sAY4QBKLmS58dpFGHgwCXQKRASR31?usp=sharing) or in a local Jupyter notebook.

2. If you're using Colab, switch to the best GPU available (go to Runtime -> change runtime type).

3. Add your OpenAI API key to the line `openai.api_key = "YOUR KEY HERE"`.

## How to Use

1. Define your `prompt`. The `prompt` is a description of what you want the trained AI to do. The more descriptive and clear you can be, the better. Additionally, set the temperature we will use to generate your dataset (high=creative, low=precise), and the number of examples you want to generate (100 is a good starting point).

For example:
```
prompt = "A model that takes in a puzzle-like reasoning-heavy question in English, and responds with a well-reasoned, step-by-step thought out response in Spanish."
temperature = .4
number_of_examples = 100
```

2. Run all the cells (stop at `Merge the model and store in Google Drive`).

*It'll take some time (from 10 minutes to a couple of hours, depending on how many examples you generate), but soon, you'll have your fine-tuned model!*

3. After your model is trained, you can use the `Run Inference` cell to test the model, and the cells below that allow you to save and load the model to and from Google Drive for later use.

## Contributions are welcome! Some ideas:
- improve the example generation pipeline for efficiency/cost reduction (using n=)
- add additional example generation prompts to create more diverse examples
- add example pruning, removing very similar examples to improve performance
- use GPT-4 to automatically choose the training hyperparameters (and potentially, even the model to fine-tune!) based on a few examples + high-level dataset details (i.e. number of examples)
- train multiple model variants and choose the one with the lowest eval loss

## License

This project is [MIT](https://github.com/mshumer/gpt-llm-trainer/blob/master/LICENSE) licensed.

## Contact

Matt Shumer - [@mattshumer_](https://twitter.com/mattshumer_)

Project Link: [https://github.com/mshumer/gpt-llm-trainer](url)

Lastly, if you want to try something even cooler than this, sign up for [Personal Assistant](https://www.hyperwriteai.com/personal-assistant) (most of my time is spent on this). It's basically an AI that can operate your web browser to complete tasks for you.

### Contributions

In this fork of the original project, significant enhancements have been made to address common challenges that arise when training a machine learning model with data generated by the model itself. These challenges include overfitting, ignoring minority classes, and amplification of biases. The specific contributions are:

- **Overfitting Mitigation**: Implemented strategies to reduce the risk of the model overfitting to its own generated data. By enhancing the diversity in generation and applying specific techniques to ensure a more generalized learning, the robustness of the model has been improved.
- **Handling Minority Classes**: Ensured that minority classes are not overlooked in the training process. By balancing classes in the dataset, the model is trained to handle various classes fairly, leading to more accurate predictions across different categories.
- **Bias Evaluation and Adjustment**: Introduced mechanisms to evaluate and adjust biases in the generated data. By implementing a systematic approach to assess and rectify biases, the model's fairness and objectivity have been enhanced.

These contributions aim to make the training process more effective, unbiased, and robust, contributing to the creation of a more reliable and accurate model.

