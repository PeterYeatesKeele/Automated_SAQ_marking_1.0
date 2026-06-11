# Automated Short Answer Question (SAQ) scoring with Large Language Models

This code was used to conduct data processing and analysis for a paper provisionally titled:
"From agreement to assessment consequences: using supervised fine-tuning to enhance consequential validity of large language model scoring of short answer questions" 
Author: Peter Yeates
Keele University School of Medicine
2026

The purpose of paper is to investigate the potential to align an LLM with human judgement by using both few-shot learning and supervised finetuning within the context of a basic science knowledge testing exam for year 1 medical students 

The workflow ingests:
a. short answer question responses by students along with associated faculty scores and feedback
b. question parameters

as .csv files. Example .csv files are included to indicate headings, but data have been redacted for privacy / intellectual property.

The workflow then: 
1. splits the data into training, validation and testing sets
2. bundles data with prompts +/- few shot examples within jsonl files
3. analyses the testing data using the base LLM under zero and few-shot conditions
4. fine-tunes the model using the training and validation datasets
5. analyses the testing data using the fine-tuned LLM under zero and few-shot conditions
6. evaluates the outputs in comparison to human scoring, including impact on pass / fail categorisation

## Installation:
The code uses calls to OpenAI models through the OpenAI SDK. You will need an OpenAI key
Once created, save your OpenAI key in .env at the point indicated

create a virtual environment in the project folder: 
python -m venv venv

activate the environment, then:
pip install -r requirements.txt

Open: saq_fine_tuning_sharing_version.ipynb

The 3rd cell in the notebook will create a folder structure within the project directory:
"# Define required directories within cwd
required_dirs = ["data", "jsonl_files", "model_outputs", "evaluation"]"

"# Create them if they do not exist
for folder in required_dirs:
    (cwd / folder).mkdir(exist_ok=True)"

Place appropriate data into this folder and update paths as required throughout the notebook
Data should involve:
1. a main data file
2. a question parameters file
with headings as indicated in the sample .csv files

Beyond this, run cells sequentially.

# Data availability:
The original student response data cannot be shared because of privacy restrictions.
