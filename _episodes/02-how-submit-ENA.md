---
title: "How to submit to ENA repository"
teaching: 10
exercises: 0
questions:
- "What is ENA?"
- "What do I submit to ENA?"
- "How can I submit?"
objectives:
- "Explain the parts of the data model: Study, Sample, Experiment, Run, Analysis."
- "Explain the different types of submissions."
keypoints:
- "European Nucleotide Archive (ENA) stores annotated DNA and RNA sequences."
- "Submissions are represented using a number of different metadata objects." 
- "Study, sample and raw reads are the objects to be submitted."
- "Submissions can be done via browser, command-line interface (raw reads only) or programmatically."
---
## European Nucleotide Archive (ENA)
The [ENA](https://www.ebi.ac.uk/ena/browser/home) is a repository providing submission of, and access to, annotated DNA and RNA sequences. 

It also stores complementary information such as experimental procedures, details of sequence assembly and other metadata related to sequencing projects.

Submissions are represented using a number of different metadata objects. Before submitting data to ENA, it is important to familiarise yourself with the ENA metadata model and what parts of your research project can be represented by which metadata objects. This will determine what you need to submit.

* For example, a publication is typically associated with a **study** (project), sequenced source material is represented using **samples**, and sequencing experiment details are captured by the **experiment** object.

* Note that data files are also submitted by associating them with metadata objects. Sequence read data is associated with **run** objects while other data files are associated with **analysis** objects. 

The full **[metadata model](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/metadata.html)** with relationships between the different types of objects is illustrated below.

![metadata_model](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/metadata_model.png)


* **Study:** A study (project) groups together data submitted to the archive and controls its release date. A study accession is typically used when citing data submitted to ENA. Note that all associated data and other objects are made public when the study is released.

* **Sample:** A sample contains information about the sequenced source material. Samples are associated with checklists, which define the fields used to annotate the samples. Samples are always associated with a taxon.

* **Experiment:** An experiment contains information about a sequencing experiment including library and instrument details.

* **Run:** A run is part of an experiment and refers to data files containing sequence reads.

* **Analysis:** An analysis contains secondary analysis results derived from sequence reads (e.g. a genome assembly),

* **Submission:** A submission contains submission actions to be performed by the archive. A submission can add more objects to the archive, update already submitted objects or make objects publicly available.

### What to submit
1. [Study](https://ena-docs.readthedocs.io/en/latest/submit/study.html) - place-holder for the project; needs to be done first

2. [Sample](https://ena-docs.readthedocs.io/en/latest/submit/samples.html) - place-holder for the biomaterial information; second thing to do

3. [Raw reads](https://ena-docs.readthedocs.io/en/latest/submit/reads.html) - both the sequencing information (Experiment) and the data files (Run); last thing to do

### Ways to submit
* [Interactive](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/interactive.html) - using browser
    * [Study](https://ena-docs.readthedocs.io/en/latest/submit/study/interactive.html)
    * [Sample](https://ena-docs.readthedocs.io/en/latest/submit/samples/interactive.html)
    * [Raw reads](https://ena-docs.readthedocs.io/en/latest/submit/reads/interactive.html)

* [Webin-CLI](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html) - command-line submission interface
    * [Raw reads](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html) only
    * validate, upload and submit in a single step
    * write a manifest file

* [Programmatic submission](https://ena-docs.readthedocs.io/en/latest/submit/reads/programmatic.html) - XML document submitted using cURL
    * [Study](https://ena-docs.readthedocs.io/en/latest/submit/study/programmatic.html)
    * [Sample](https://ena-docs.readthedocs.io/en/latest/submit/samples/programmatic.html)
    * [Raw reads](https://ena-docs.readthedocs.io/en/latest/submit/reads/programmatic.html)
