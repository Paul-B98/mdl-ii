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

Bei der Evaluation werden die erstellten Modelle  mit den Modellen von Salesforce und dem Software Engineering for Business Information Systems (SEBIS) Fachbereich der TU München verglichen. Bei den Salesforce Modellen wird ein spezialisiertes CodeT5 als Model verwendet. Hingegen wird vom SEBIS nur T5 als Basismodell verwendet. [^6] [^8]

Die Evaluation wurde auf einem System mit einer Nvidia RTX 4070 Ti als GPU und einem Ryzen 9 7900X als CPU durchgeführt. Alternativ kam ein System mit einem Intel Xeon E5-2690v3 als CPU und einer Nvidia Tesla K80 zum Einsatz. Bei dem für die Evaluation verwendeten Datensatz handelt es sich um den Testdatensatz des CodeSeachNet Datensatzes. Dieser umfasst in der aufbereiteten Form ungefähr 15.000 Daten [^1]. 

| Modell | BLEU[^9] [^90] | TER[^10] | chrF[^11] [^110] | Rouge1[^12] | RougeL[^13] | Laufzeit |
| ------ | ---- | --- | ---- | ------ | ------ | -------- |
| CodeT5-base-sum-python[^14] | 23.564 |  93.313 | 39.069 | 0.489 | 0.462 | 0.105 ±0.001 |
| CodeT5-base-multi-sum[^15]  | 23.985 |  88.667 | 39.318 | 0.491 | 0.463 | 0.106 ±0.001 |
| Code-Trans-S-ST[^16]        |  5.495 | 103.981 | 25.007 | 0.287 | 0.256 | 0.078 ±0.002 |
| Code-Trans-S-TF[^17]        | 21.093 |  71.626 | 37.157 | 0.476 | 0.448 | 0.039 ±0.000 |
| Code-Trans-S-MT[^18]        |  5.450 |  89.910 | 20.280 | 0.295 | 0.276 | 0.030 ±0.001 |
| Code-Trans-S-MT-TF[^19]     | 16.378 |  76.738 | 34.692 | 0.452 | 0.421 | 0.025 ±0.001 |
| Code-Trans-B-ST[^10]        |  4.638 | 102.021 | 23.194 | 0.263 | 0.234 | 0.083 ±0.002 |
| Code-Trans-B-TF[^21]        | 21.671 |  71.560 | 37.954 | 0.485 | 0.457 | 0.035 ±0.000 |
| Code-Trans-B-MT[^22]        |  2.957 |  93.160 | 15.566 | 0.221 | 0.208 | 0.038 ±0.001 |
| Code-Trans-B-MT-TF[^23]     | 13.766 |  78.742 | 33.452 | 0.443 | 0.410 | 0.057 ±0.001 |
| Code-Trans-L-TF[^24]        | 23.306 |  69.745 | 38.984 | 0.497 | 0.470 | 0.102 ±0.001 |
| Code-Trans-L-MT[^25]        | 13.487 |  79.615 | 32.527 | 0.433 | 0.401 | 0.089 ±0.002 |
| Code-Trans-L-MT-TF[^26]     | 16.362 |  80.671 | 35.033 | 0.445 | 0.412 | 0.124 ±0.001 |
| **Fine Tuned CodeT5+ 220m***| 25.245 |  40.596 | 66.514 | 0.515 | 0.488 | 0.110 ±0.000 |



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

@misc{elnaggar2021codetrans,
    title={CodeTrans: Towards Cracking the Language of Silicon's Code Through Self-Supervised Deep Learning and High Performance Computing}, 
    author={Ahmed Elnaggar and Wei Ding and Llion Jones and Tom Gibbs and Tamas Feher and Christoph Angerer and Silvia Severini and Florian Matthes and Burkhard Rost},
    year={2021},
    eprint={2104.02443},
    archivePrefix={arXiv},
    primaryClass={cs.SE}
}

@inproceedings{lin-hovy-2003-automatic,
    title="Automatic Evaluation of Summaries Using N-gram Co-occurrence Statistics",
    author="Lin, Chin-Yew  and Hovy, Eduard",
    booktitle="Proceedings of the 2003 Human Language Technology Conference of the North {A}merican Chapter of the Association for Computational Linguistics",
    year="2003",
    url="https://aclanthology.org/N03-1020",
    pages="150--157",
}

@inproceedings{lin-och-2004-automatic,
    title="Automatic Evaluation of Machine Translation Quality Using Longest Common Subsequence and Skip-Bigram Statistics",
    author="Lin, Chin-Yew  and Och, Franz Josef",
    booktitle="Proceedings of the 42nd Annual Meeting of the Association for Computational Linguistics ({ACL}-04)",
    month=jul,
    year="2004",
    address="Barcelona, Spain",
    url="https://aclanthology.org/P04-1077",
    doi="10.3115/1218955.1219032",
    pages="605--612",
}

@inproceedings{10.3115/1073083.1073135,
    author={Papineni, Kishore and Roukos, Salim and Ward, Todd and Zhu, Wei-Jing},
    title={BLEU: A Method for Automatic Evaluation of Machine Translation},
    year={2002},
    publisher={Association for Computational Linguistics},
    address={USA},
    url={https://doi.org/10.3115/1073083.1073135},
    doi={10.3115/1073083.1073135},
    abstract={Human evaluations of machine translation are extensive but expensive. Human evaluations can take months to finish and involve human labor that can not be reused. We propose a method of automatic machine translation evaluation that is quick, inexpensive, and language-independent, that correlates highly with human evaluation, and that has little marginal cost per run. We present this method as an automated understudy to skilled human judges which substitutes for them when there is need for quick or frequent evaluations.},
    booktitle={Proceedings of the 40th Annual Meeting on Association for Computational Linguistics},
    pages={311–318},
    numpages={8},
    location={Philadelphia, Pennsylvania},
    series={ACL '02}
}

@inproceedings{popovic-2015-chrf,
    title = "chr{F}: character n-gram {F}-score for automatic {MT} evaluation",
    author = "Popovi{\'c}, Maja",
    booktitle = "Proceedings of the Tenth Workshop on Statistical Machine Translation",
    month = sep,
    year = "2015",
    address = "Lisbon, Portugal",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/W15-3049",
    doi = "10.18653/v1/W15-3049",
    pages = "392--395",
}

@inproceedings{popovic-2017-chrf,
    title = "chr{F}++: words helping character n-grams",
    author = "Popovi{\'c}, Maja",
    booktitle = "Proceedings of the Second Conference on Machine Translation",
    month = sep,
    year = "2017",
    address = "Copenhagen, Denmark",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/W17-4770",
    doi = "10.18653/v1/W17-4770",
    pages = "612--618",
}

@misc{post2018clarity,
    title={A Call for Clarity in Reporting BLEU Scores}, 
    author={Matt Post},
    year={2018},
    eprint={1804.08771},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}

@inproceedings{snover-etal-2006-study,
    title = "A Study of Translation Edit Rate with Targeted Human Annotation",
    author = "Snover, Matthew  and Dorr, Bonnie  and Schwartz, Rich  and Micciulla, Linnea  and Makhoul, John",
    booktitle = "Proceedings of the 7th Conference of the Association for Machine Translation in the Americas: Technical Papers",
    month = aug # " 8-12",
    year = "2006",
    address = "Cambridge, Massachusetts, USA",
    publisher = "Association for Machine Translation in the Americas",
    url = "https://aclanthology.org/2006.amta-papers.25",
    pages = "223--231",
    abstract = "We examine a new, intuitive measure for evaluating machine-translation output that avoids the knowledge intensiveness of more meaning-based approaches, and the labor-intensiveness of human judgments. Translation Edit Rate (TER) measures the amount of editing that a human would have to perform to change a system output so it exactly matches a reference translation. We show that the single-reference variant of TER correlates as well with human judgments of MT quality as the four-reference variant of BLEU. We also define a human-targeted TER (or HTER) and show that it yields higher correlations with human judgments than BLEU{---}even when BLEU is given human-targeted references. Our results indicate that HTER correlates with human judgments better than HMETEOR and that the four-reference variants of TER and HTER correlate with human judgments as well as{---}or better than{---}a second human judgment does.",
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
[^8]: CodeTrans: Towards Cracking the Language of Silicon's Code Through Self-Supervised Deep Learning and High Performance Computing
[^9]: BLEU: A Method for Automatic Evaluation of Machine Translation
[^90]: A Call for Clarity in Reporting BLEU Scores
[^10]: A Study of Translation Edit Rate with Targeted Human Annotation
[^11]: chrF: character n-gram F-score for automatic MT evaluation
[^110]: chrF++: words helping character n-grams
[^12]: Automatic Evaluation of Summaries Using N-gram Co-occurrence Statistics
[^13]: Automatic Evaluation of Machine Translation Quality Using Longest Common Subsequence and Skip-Bigram Statistics
[^14]: https://huggingface.co/Salesforce/codet5-base-codexglue-sum-python
[^15]: https://huggingface.co/Salesforce/codet5-base-multi-sum
[^16]: https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python
[^17]: https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_transfer_learning_finetune
[^18]: https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_multitask
[^19]: https://huggingface.co/SEBIS/code_trans_t5_small_code_documentation_generation_python_multitask_finetune
[^20]: https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python
[^21]: https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_transfer_learning_finetune
[^22]: https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_multitask
[^23]: https://huggingface.co/SEBIS/code_trans_t5_base_code_documentation_generation_python_multitask_finetune
[^24]: https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_transfer_learning_finetune
[^25]: https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_multitask
[^26]: https://huggingface.co/SEBIS/code_trans_t5_large_code_documentation_generation_python_multitask_finetune
