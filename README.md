# Fallstudie des Moduls Machine & Deep Learning II

## Kontext und Aufgabenstellung

Die [Aufgabenstellung](./docs/task.md) der Fallstudie ist das erarbeiten einer KI welche automatisiert zu Python-Quellcode Docstrings generiert.

## Dokumentation

Weitere information zu dem Projekt sind der [Dokumentation](./docs/README.md) zu entnehmen.

## Daten 

Als Basis für die Daten dient der Datensatz der [CodeSearchNet Challenge](https://arxiv.org/pdf/1909.09436.pdf). Für die Fallstudie wurde eine Angepasste Variante des [Datensatz](https://huggingface.co/datasets/semeru/code-text-python) vom SEMERU Lab verwendet.

## Models



## Evaluation

## Installation

```bash
conda create -n codetf python=3.10
pip install -q -U git+https://github.com/Paul-B98/CodeTF.git
pip install -q -U git+https://github.com/huggingface/transformers.git
pip install -q -U git+https://github.com/huggingface/peft.git
pip install -q -U git+https://github.com/huggingface/accelerate.git
```