# Fallstudie des Moduls Machine & Deep Learning II

## Kontext und Aufgabenstellung

Die [Aufgabenstellung](./docs/task.md) der Fallstudie ist das erarbeiten einer KI welche automatisiert zu Python-Quellcode Docstrings generiert.

## Dokumentation

Weitere information zu dem Projekt sind der [Dokumentation](./docs/README.md) zu entnehmen.

## Daten 

Als Basis für die Daten dient der Datensatz der [CodeSearchNet Challenge](https://arxiv.org/pdf/1909.09436.pdf). Für die Fallstudie wurde eine Angepasste Variante des [Datensatz](https://huggingface.co/datasets/semeru/code-text-python) vom SEMERU Lab verwendet.

## Models



## Evaluation

Models:
https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python
https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_transfer_learning_finetune
https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_multitask
https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_multitask_finetune

https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python
https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_transfer_learning_finetune
https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_multitask
https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_multitask_finetune

https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_transfer_learning_finetune
https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_multitask
https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_multitask_finetune

https://huggingface.co/Salesforce/codet5-base-codexglue-sum-python
https://huggingface.co/Salesforce/codet5-base-multi-sum


## Installation

```bash
conda create -n codetf python=3.10
pip install -q -U git+https://github.com/Paul-B98/CodeTF.git
pip install -q -U git+https://github.com/huggingface/transformers.git
pip install -q -U git+https://github.com/huggingface/peft.git
pip install -q -U git+https://github.com/huggingface/accelerate.git
pip install sentencepiece matplotlib
```
