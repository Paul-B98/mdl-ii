# Fallstudie des Moduls Machine & Deep Learning II

## Kontext und Aufgabenstellung

Die [Aufgabenstellung](./docs/task.md) der Fallstudie ist das erarbeiten einer KI welche automatisiert zu Python-Quellcode Docstrings generiert.

## Dokumentation

Weitere information zu dem Projekt sind der [Dokumentation](./docs/README.md) zu entnehmen.

## Daten 

Der verwendete Datensatz ist dabei der CodeSearchNet[^1] Datensatz, welcher auch in der CodeXGlue[^2] Challenge von Microsoft für Quellcode-zu-Text Aufgaben verwendet wurde. Hierbei wird eine angepasste Variante des Datensatzes verwendet. Bei den Anpassungen handelt es sich um Vorverarbeitungen durch das SEMERU Lab. Der vorverarbeitete Datensatz umfasst dabei Methoden und Funktionen, die in der Programmiersprache Python entwickelt wurden, sowie zugehörige Kommentare. [^3]

### Data Preparation 

Zusätzlich zu dem Entfernen von nicht benötigten Features wurde ebenfalls Datensätze entfernt welche Python 2 Quellcode enthalten. Zudem wurde der Docsting aus dem Feature **Code** entfernt.

## Modeling

Im Rahmen des Modellings werden Techniken aus dem Natural Language Processings zum Einsatz kommen. Zusätzlich wird das Transferlernen mittels vortrainierter Modelle umgesetzt. Die verwendeten Modelle werden dabei im Einzelnen in dem Modellierungsabschnitt erläutert. Zum Durchführen der Arbeit wird auf die Bibliothek CodeTF zurückgegriffen, an der im Laufe der Fallstudie mitgearbeitet wurde [^4].

Im Zusammenhang mit dieser Fallstudie wurde das CodeT5+ Modell mit 220 Millionen Parameter verwendet, um ein Fine Tuning durchzuführen. Dabei wurde sich aufgrund von Speicher- sowie zeitlichen Limitierungen für das Modell entscheiden. Dieses Modell wurde dann mittels des aufbereiteten CodeSearchNet Datensatz für zwei Epochen mit einer Nvidia Tesla K80 asl GPU weiter trainiert. Das Training wurde mit Standardparametern durchgeführt. Nur die Epochen wurden auf zwei reduziert, um die Trainingszeit auf ungefähr 26 Stunden zu reduzieren. [^5] [^6] [^7] 

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
pip install salesforce-codetf sentencepiece matplotlib
```

# References

## Bibtex

```bibtex
@article{DBLP:journals/corr/abs-1909-09436,
    author={Hamel Husain and Ho{-}Hsiang Wu and Tiferet Gazit and Miltiadis Allamanis and Marc Brockschmidt},
    title={CodeSearchNet Challenge: Evaluating the State of Semantic Code Search},
    journal={CoRR},
    volume={abs/1909.09436},
    year={2019},
    url={http://arxiv.org/abs/1909.09436},
    eprinttype={arXiv},
    eprint={1909.09436},
    timestamp={Tue, 24 Sep 2019 11:33:51 +0200},
    biburl={https://dblp.org/rec/journals/corr/abs-1909-09436.bib},
    bibsource={dblp computer science bibliography, https://dblp.org}
}

@misc{lu2021codexglue,
    title={CodeXGLUE: A Machine Learning Benchmark Dataset for Code Understanding and Generation}, 
    author={Shuai Lu and Daya Guo and Shuo Ren and Junjie Huang and Alexey Svyatkovskiy and Ambrosio Blanco and Colin Clement and Dawn Drain and Daxin Jiang and Duyu Tang and Ge Li and Lidong Zhou and Linjun Shou and Long Zhou and Michele Tufano and Ming Gong and Ming Zhou and Nan Duan and Neel Sundaresan and Shao Kun Deng and Shengyu Fu and Shujie Liu},
    year={2021},
    eprint={2102.04664},
    archivePrefix={arXiv},
    primaryClass={cs.SE}
}

@misc{nghi2023codetf,
    title={CodeTF: A Transformer-based Library for CodeLLM & Code Intelligence}, 
    author={Nghi D. Q. Bui, Henry Le, Yue Wang, Akhilesh Deepak Gotmare, Junnan Li, Steven Hoi.},
    year={2023},
    eprint={2209.09019},
    archivePrefix={arXiv},
    primaryClass={cs.CV}
}

@article{DBLP:journals/corr/abs-1910-10683,
  author={Colin Raffel and Noam Shazeer and Adam Roberts and Katherine Lee and Sharan Narang and Michael Matena and Yanqi Zhou and Wei Li and Peter J. Liu},
  title={Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer},
  journal={CoRR},
  volume={abs/1910.10683},
  year={2019},
  url={http://arxiv.org/abs/1910.10683},
  eprinttype={arXiv},
  eprint={1910.10683},
  timestamp={Fri, 05 Feb 2021 15:43:41 +0100},
  biburl={https://dblp.org/rec/journals/corr/abs-1910-10683.bib},
  bibsource={dblp computer science bibliography, https://dblp.org}
}

@misc{wang2021codet5,
    title={CodeT5: Identifier-aware Unified Pre-trained Encoder-Decoder Models for Code Understanding and Generation}, 
    author={Yue Wang and Weishi Wang and Shafiq Joty and Steven C. H. Hoi},
    year={2021},
    eprint={2109.00859},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}

@misc{wang2023codet5,
      title={CodeT5+: Open Code Large Language Models for Code Understanding and Generation}, 
      author={Yue Wang and Hung Le and Akhilesh Deepak Gotmare and Nghi D. Q. Bui and Junnan Li and Steven C. H. Hoi},
      year={2023},
      eprint={2305.07922},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}


```

## footnotes
[^1]: CodeSearchNet Challenge: Evaluating the State of Semantic Code Search
[^2]: CodeXGLUE: A Machine Learning Benchmark Dataset for Code Understanding and Generation
[^3]: https://huggingface.co/datasets/semeru/code-text-python
[^4]: CodeTF: A Transformer-based Library for CodeLLM & Code Intelligence
[^5]: Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer
[^6]: CodeT5: Identifier-aware Unified Pre-trained Encoder-Decoder Models for Code Understanding and Generation
[^7]: CodeT5+: Open Code Large Language Models for Code Understanding and Generation
[^]:
[^]:
[^]:
[^]:
[^]:

