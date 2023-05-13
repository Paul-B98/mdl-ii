# Fallstudie des Moduls Machine & Deep Learning II

## Kontext

Um Programmcode einfacher wartbar und nachvollziehbar zu gestalten, kann er u.a. mit Kommentaren versehen werden. Die Vorteile liegen auf der Hand:
* Schnelleres Verständnis (von fremdem Code) 
  * Spart Zeit bei der (erneuten) Einarbeitung
* Besseres Verständnis: Kompakter bzw. komplexer Code wird verständlich natürlichsprachlich angereichert 
  * Ggf. falsche Auffassungen von der Funktionsweise werden ex ante eliminiert

### Compliances und regulatorische Vorgaben

Mitunter kann es auch vorkommen, dass unternehmensinterne Bestimmungen (Compliances) die Kommentierung von Code vorschreiben oder gar regulatorische Anforderungen für kritische Anwendungen bspw. im Versicherungs- bzw. Bankenwesen eine ausführliche Kommentierung von Programmcode verpflichtend vorgeben

### Herausforderungen bei der Kommentierung von Code

* Programmcode wird überarbeitet ohne, dass Kommentare angepasst werden
* Häufig fehlende Kommentare aufgrund vielfältiger Gründe:
  * Nicht ausreichend Zeit vorhanden bspw. im Projekt
  * Persönliche Antipathie einzelner Entwickler:innen gegenüber Kommentaren
  * Kommentare wurden schlicht vergessen

## Aufgabe

Als Hausarbeit ist folgende Fallstudie zu bearbeiten: Automatische Generierung von One-line und Multi-line docstrings für Python Code

### Zielsetztung
1. Erstellung eines Deep Neural Networks zur automatisierten Erstellung von 
Code Kommentaren
    * Ausschließlich für Python Programmcode
    * Beschränkt auf Methoden / Funktionen
    * Generierung von Kommentaren im docstring1 Format  One-line und Multi-line  docstring
1. Evaluation des Modells mit geeigneten Metriken des NLP
1. Anwendung des Modells auf das/die eigene/n zuvor erstellte/n Jupyter Notebook/s

## Rahmenbedingungen
### Technologien

* Beliebiges Computational Backend, z.B. TensorFlow, PyTorch etc.
* Bei Bedarf Verwendung von High-Level APIs wie bspw. Keras
* Keinerlei Einschränkungen von Third-Party Libraries
  * Ausgeschlossen sind lediglich Auto ML-Libraries
* Beliebige Entwicklungsplattform, z. B.:
  * Lokale Entwicklung: Nur empfehlenswert auf Tower PC mit leistungsfähiger, dedizierter GPU
  * Beliebiger Hosted Jupyter Notebook Service, z. B. Kaggle Kernel, Google Colab
  * Beliebiger anderer Cloud Dienst, der über eine API ansprechbar ist

### Methodik

* Umsetzung mittels beliebiger Netzarchitektur
  * Reccurent Neural Network (RNN)
  * Encoder Decoder Architecture
  * Sequence-to-Sequence Model (Seq2Seq)
  * ...
* Nutzung von vortrainierten Backbone-Networks ist erlaubt
* Einsatz weiterführender, nicht in der Vorlesung besprochener Methoden und Modelle ist erlaubt und erwünscht

### Datenbasis

Frei wählbare Datenbasis, die für die Aufgabenstellung adäquat ist.

## Evaluation

* Beliebiges, selbst gewähltes Test Dataset
* Keinerlei Vorgaben bzgl. der Metriken 
  * Jene Metrik(en) wählen, die für die Aufgabenstellung angemessen erscheinen

## Dokumentation

Weitere information zu dem Projekt sind der [Dokumentation](./docs/README.md) zu entnehmen.