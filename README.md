# Analysing performance of LLMs on sentiment analysis of X data for US24 elections

!important - source of data citation: https://arxiv.org/abs/2411.00376

## TLDR: taken subset of tweets from mentioned us-elections dataset
and ran: 
- `tweetnlp` (mentioned as `nn` in the plot)
- `gpt-4o`
- `gpt-4o-mini`
- `claude-3-5-sonnet-latest`
- `claude-3-5-haiku-latest`
- `gemini-1.5-pro`
- `gemini-1.5-flash`

Result confusion matrix after majority voting for GT:
![result-confusion-matrix](./confusion_matrix.png)

## Contents of notebooks:

- 001 loads and extracts valid representable columns;
  - outputs full time period `data.csv` (not included in GDrive, use code to produce);
  - outputs small time period after 1st Oct `data_small.csv`
- 002 loads `data_small.csv` and runs Semantic Analysis using cardiffnlp/twitter-roberta-base-sentiment-latest (tweetnlp pypi); 
  - outputs `data_sent.csv`
- 003 loads `data_small.csv` and runs `emotion` detection using `tweetnlp`:
  - outputs `data_emotion.csv`
- 004 loads `data_small.csv` and runs `irony` detection using `tweetnlp`:
  - outputs `data_irony.csv`
- 005 loads `data_small.csv` and runs `hate speech` detection using `tweetnlp`:
  - outputs `data_hate.csv`
- 006 loads `data_small.csv` and runs `offensive speech` detection using `tweetnlp`:
  - outputs `data_offensive.csv`
- 007 loads `data_small.csv` and runs `NER`(name entity recognition) detection using `tweetnlp`:
- 008 loads `data_small.csv` and runs `topic` detection using `tweetnlp`:
  - outputs `data_topic.csv`
- 009 explores `data_topic` distribution;
- 010 uses `data_small.csv` and runs LLMs:
  - produces `models_results.json`
- 011 data exploration of `models_results.json` with `data_sent.csv` and `data_small.csv`


## Original setup for personal running
```
mkdir project
cd project
git clone https://github.com/sinking8/usc-x-24-us-election.git
git clone https://github.com/liepieshov/genai-analysis-x-24-us-elections.git
cd genai-analysis-x-24-us-elections

# start using notebooks
# note: the requirements.txt is not listed, but they are quite straitforward.
```


## Output data

License:

This dataset is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License (CC BY-NC-SA 4.0). By using this dataset, you agree to abide by the stipulations in the license and cite the following manuscript:

https://arxiv.org/abs/2411.00376


Output data files for all notebooks (except `data.csv` from 001_*.nb):
- https://drive.google.com/drive/folders/1wfJte4qq8TdC11KqTvj4RBEXvZBXPvb-?usp=sharing

```
# file hashes
>>> md5 ./*
MD5 (./README_LICENCE.md) = 3a3921a8880f55adbee7ba9dcca44ac4
MD5 (./data.csv) = a484358852dd39f7d8af8ec79152104d
MD5 (./data_emotion.csv) = c6b4d86da6f052c82bd1d2eeb1ef5b44
MD5 (./data_hate.csv) = 1553d31ff3e7588ca8d414b60b043862
MD5 (./data_irony.csv) = 2e678ce8a9f8edf9f280c08e987a1175
MD5 (./data_offensive.csv) = 40adfc09cf7c81d473644ae41740e16d
MD5 (./data_sent.csv) = a1de94f54453ef55a945649833b13f22
MD5 (./data_small.csv) = 167992af113db29b9c7f2d34767855df
MD5 (./data_topic.csv) = f83105ee6329835b672629bfc6b946a4
MD5 (./models_results.json) = 03bfb99a559e89d69c173e98410bcc74
```
