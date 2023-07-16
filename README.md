# Fallstudie des Moduls Machine & Deep Learning II

## Kontext und Aufgabenstellung

Die [Aufgabenstellung](./docs/task.md) der Fallstudie ist das erarbeiten einer KI welche automatisiert zu Python-Quellcode Docstrings generiert.

## Dokumentation

Weitere information zu dem Projekt sind der [Dokumentation](./docs/README.md) zu entnehmen.

## Daten 

Der verwendete Datensatz ist dabei der CodeSearchNet[^1] Datensatz, welcher auch in der CodeXGlue[^2] Challenge von Microsoft für Quellcode-zu-Text Aufgaben verwendet wurde. Hierbei wird eine angepasste Variante des Datensatzes verwendet. Bei den Anpassungen handelt es sich um Vorverarbeitungen durch das SEMERU Lab. Der vorverarbeitete Datensatz umfasst dabei Methoden und Funktionen, die in der Programmiersprache Python entwickelt wurden, sowie zugehörige Kommentare.


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
pip install salesforce-codetf sentencepiece matplotlib
```

# Resources

[^1]: 
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
    ```

[^2]: 
    ```bibtex
    @misc{lu2021codexglue,
        title={CodeXGLUE: A Machine Learning Benchmark Dataset for Code Understanding and Generation}, 
        author={Shuai Lu and Daya Guo and Shuo Ren and Junjie Huang and Alexey Svyatkovskiy and Ambrosio Blanco and Colin Clement and Dawn Drain and Daxin Jiang and Duyu Tang and Ge Li and Lidong Zhou and Linjun Shou and Long Zhou and Michele Tufano and Ming Gong and Ming Zhou and Nan Duan and Neel Sundaresan and Shao Kun Deng and Shengyu Fu and Shujie Liu},
        year={2021},
        eprint={2102.04664},
        archivePrefix={arXiv},
        primaryClass={cs.SE}
    }
    ```