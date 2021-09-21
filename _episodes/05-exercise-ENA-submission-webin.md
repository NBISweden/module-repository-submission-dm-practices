---
title: "(Optional) Exercise - submission to ENA using Webin-CLI"
teaching: 10
exercises: 40
questions:
- "I have my datasets, what is the submission process?"
objectives:
- "Explain the steps of submission to European Nucleotide Archive."
- "Do a submission using the Webin Command Line Interface(Webin-CLI)"
keypoints:
- "When in doubt on how to submit, go to the test submission site and do a test submission: [https://wwwdev.ebi.ac.uk/ena/submit/webin](https://wwwdev.ebi.ac.uk/ena/submit/webin)"
- "The steps of submission process are:  
    1. In the browser: Register study level information and samples
    2. Create manifest file(s) - envelope / metadata for sequence files
    3. Validate and upload manifest file(s) and sequence file(s)"
- "The whole process of submission, from file upload to receiving an accession number takes time.  Do not do this late in the project, when publishers require that you publish datasets before review and deadline is 24 hours."
- "If you ever are stuck, contact us data stewards at NBIS by sending an email to **[data@nbis.se](mailto:data@nbis.se)** or ask for a consultation via **[our homepage](https://nbis.se/support/supportform/index.php?form=consultation)**."
---
> ## Prerequisites
> * This exercise requires a sequence file, A_Wt.fastq.gz, found in the subfolder `dm-practices/7-repository-submission/data/`, available for download at [https://doi.org/10.17044/scilifelab.14301317](https://doi.org/10.17044/scilifelab.14301317).
>
> * In the folder `dm-practices/7-repository-submission/`, create a subfolder named `prg`, (i.e. `Desktop/dm-practices/7-repository-submission/prg`).
> 
> * Webin-CLI requires that you have Java installed before you can run it. You should have version 1.8 or newer, which can be [downloaded from Java](https://java.com/en/download/).
>
> * You will also need to download and install a Java Runtime Environment (JRE) and we recommend Zulu Open JDK available at [https://www.azul.com/downloads/?package=jdk](https://www.azul.com/downloads/?package=jdk)
> 
> * Download Webin-CLI Java jar file from its [GitHub repository](https://github.com/enasequence/webin-cli/releases/latest), and put it in `dm-practices/7-repository-submission/prg/`.
>
{: .prereq}

## (Optional) Do a submission to ENA using Webin-CLI
* Webin command line submission interface allows for automatic validation. Unlike other ENA submission routes, you do not need to pre-upload your files when using Webin-CLI.

* Use the test submission site when you want to test, and the production site for real submissions:
    * Test site: [https://wwwdev.ebi.ac.uk/ena/submit/webin](https://wwwdev.ebi.ac.uk/ena/submit/webin)
    * Production site: [https://www.ebi.ac.uk/ena/submit/webin](https://www.ebi.ac.uk/ena/submit/webin)
    * *Note: The test service is restarted every night, any submissions made to the test service will be removed by the following day. Hence, do not start a test submission one day, and expect to continue the next day.*

* Submission steps:
    1. In the browser:
       1. Login 
       2. Register study - Provide study level information
       3. Register sample(s) - Provide sample metadata
    2. Create manifest file(s) - envelope / metadata for sequence files
    3. Validate and upload manifest file(s) and sequence file(s))

### 1. In the browser
* Go to the test service: [https://wwwdev.ebi.ac.uk/ena/submit/webin](https://wwwdev.ebi.ac.uk/ena/submit/webin) and log in with your Webin username and password. 

  ![webin-login](../fig/webin-login.jpg)

  To the left, in the top of the welcome page, there is a dashboard menu which will expand when you click on it. 

  ![dashboard](../fig/dashboard.jpg)

  #### [Register study (project)](https://ena-docs.readthedocs.io/en/latest/submit/study/interactive.html) 
  * Click on the Dashboard menu and select **Register Study (Project)**

    > ## Picture
    > ![dashboard-register-study](../fig/dashboard-register-study.jpg)
    {: .solution}

  * Enter the following information
    * **Release date**: 10-Oct-2022
    * **Short descriptive study title**: VEGFR2 Y949F mutation
    * **Study Name**: VEGFR2
    * **Detailed study abstract**: RNA sequencing of lung tissue from transgenic mice in order to investigate the effect of a single tyrosine to phenylalanine exchange in the endothelial receptor VEGFR2 at position Y949.
  * Click on **Submit**
  * Verify that the submission was successful in the pop-up **Submission** window, then click on **Close**

    > ## Solution
    > ![register-study](../fig/register-study.jpg)
  {: .solution}

  #### [Register samples](https://ena-docs.readthedocs.io/en/latest/submit/samples/interactive.html) 
  * Click on the Dashboard menu and select **Register Samples**
    > ## Picture
    > ![dashboard-register-samples](../fig/dashboard-register-samples.jpg)
    {: .solution}

  * This will lead to two options, either download a spreadsheet to register samples or the reverse, i.e., upload a filled spreadsheet. Typically you do not have a spreadsheet to begin with, but since we have produced one in the [OpenRefine module](https://nbisweden.github.io/module-openrefine-dm-practices/), we can skip ahead and select the upload option.

    > ## Picture
    > ![sample-submission-choice](../fig/sample-submission-choice.jpg)
    {: .solution}

  * Select the file `ENA_samples_workshop_DM_practices.tsv` from your computer (if doing this excercise independent from previous course modules, download the file first from [here](../files/ENA_samples_workshop_DM_practices.tsv)).

  * Click on **Submit Completed Spreadsheet**. 

  * Verify that the submission was successful in the pop-up **Submission** window, then click on **Close**

    > ## Picture
    > ![sample-submission-submit](../fig/sample-submission-submit.jpg)
    {: .solution}

### 2. [Prepare manifest file](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html#stage-2-prepare-the-files)

* The set of files that are part of the submission must be specified using a manifest file. The manifest file has two columns separated by a tab (or any whitespace characters):

  * Field name (first column): case insensitive field name
  * Field value (second column): field value  

* The following metadata fields are supported in the manifest file:
  * STUDY: Study accession or unique name (alias)
  * SAMPLE: Sample accession or unique name (alias)
  * NAME: Unique experiment name
  * PLATFORM: [See permitted values](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html#platform). Not needed if INSTRUMENT is provided.
  * INSTRUMENT: [See permitted values](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html#instrument)
  * INSERT_SIZE: Insert size for paired reads
  * LIBRARY_NAME: Library name (optional)
  * LIBRARY_SOURCE: [See permitted values](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html#source)
  * LIBRARY_SELECTION: [See permitted values](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html#selection)
  * LIBRARY_STRATEGY: [See permitted values](https://ena-docs.readthedocs.io/en/latest/submit/reads/webin-cli.html#strategy)
  * DESCRIPTION: free text library description (optional)

* The following file name fields are supported in the manifest file:
  * BAM: Single BAM file
  * CRAM: Single CRAM file
  * FASTQ: Single fastq file

* In a text editor such as Notepad, create a manifest file for the A_Wt sequence file (dm-practices/7-repository-submission/data/A_Wt_manifest.txt), write the following information:  
  >   STUDY     
      SAMPLE    
      INSTRUMENT  Illumina HiSeq 2500  
      LIBRARY_SOURCE  TRANSCRIPTOMIC  
      LIBRARY_SELECTION   other  
      LIBRARY_STRATEGY    RNA-Seq  
      FASTQ A_Wt.fastq.gz  

  The field values for STUDY and SAMPLE needs to be collected from your submission:
  * In the browser, where you submitted the study and samples, go to the Dashboard menu and click on the `Studies Report`
    > ## Picture Dashboard Studies Report
    > ![study-report](../fig/study-report.jpg)
    {: .solution}

  * Copy the accession number (starting with PRJEB) into the manifest file as the STUDY field value.
  * Go back to the Dashboard menu and click on the `Samples report`
    > ## Picture Dashboard Samples Report
    > ![samples-report](../fig/samples-report.jpg)
    {: .solution}

  * Locate the accession number (starting with ERS) for wt_A and copy this into the manifest file as the SAMPLE field value.
  * Save the manifest file

    > ## Solution
    > See an example manifest file [here](../files/A_Wt_manifest.txt) but note that STUDY and SAMPLE have no field values since this is unique to each study and sample submission and needs to be entered manually.
    {: .solution}

### 3. [Validate and submit the manifest file and the sequence file](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html#stage-3-validate-and-submit-files)

Open the Command Prompt window and go to the folder `dm-practices/7-repository-submission/` on your Desktop using the command `cd Desktop\dm-practices\7-repository-submission`.

<!--- ![cmd-cd](../fig/cmd-cd.jpg) Need update of pic --->

* *Note for **Mac** users: Please use forward slash, i.e. write the command `cd Desktop/dm-practices/7-repository-submission/`* 

In order to use Webin-CLI we need to give instructions on who we are and what we want to do. This is done using `options`:

* In order to see which options are available, type the following command in the Command Prompt window 

  > Windows: `java -jar prg\webin-cli-3.4.0.jar -help`  
  > Mac: `java -jar prg/webin-cli-3.4.0.jar -help`

Out of these, we will make use of the following options:

  `-context`: the submission type (genome, transcriptome, sequence or reads)  
  `-userName`: the Webin submission account name.  
  `-password`: the Webin submission account password.  
  `-manifest`: the manifest file name.  
  `-outputDir`: directory for output files.  
  `-inputDir`: input directory for files declared in manifest file.  
  `-validate`: validates the files defined in the manifest file.  
  `-submit`: validates and submits the files defined in the manifest file.  
  `-test`: use Webin test service instead of the production service. 

Please note that the Webin upload area is shared between test and production services, and that test submission files will not be archived.  

For more details about the command line options of Webin-CLI, please follow this link: [https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html#command-line-options](https://ena-docs.readthedocs.io/en/latest/submit/general-guide/webin-cli.html#command-line-options). 

First we will do a validation (-validate option) to the test server (-test option), using `data` folder as both input and output directory. 
* Copy or type the command below, and replace the `Webin-XXX` and `myPassword` with your own webin username and password, respectively:

  > Windows: `java -jar prg\webin-cli-3.4.0.jar -context reads -userName Webin-XXXXX -password myPassword -manifest A_Wt_manifest.txt -outputDir data -inputDir data -validate -test`
  > 
  > Mac: `java -jar prg/webin-cli-3.4.0.jar -context reads -userName Webin-XXXXX -password myPassword -manifest A_Wt_manifest.txt -outputDir data -inputDir data -validate -test`

* Press <kbd>Enter</kbd> 
* If the validation is successful the last output row will read:  
  > INFO : The submission has been validated successfully.

When the validation is successful, it is time to do a submit instead of a validation (-submit option instead of -validate). We will still use the test server, and the same input and output directories as for the validation step. Try to write the command yourself or take a peak at the solution below.

  > ## Solution
  >  Windows: `java -jar prg\webin-cli-3.4.0.jar -context reads -userName Webin-XXXXX -password myPassword -manifest A_Wt_manifest.txt -outputDir data -inputDir data -submit -test`
  >
  > Mac: `java -jar prg/webin-cli-3.4.0.jar -context reads -userName Webin-XXXXX -password myPassword -manifest A_Wt_manifest.txt -outputDir data -inputDir data -submit -test`
  {: .solution}

* The processing will take a while but since the validation was successful, it is only the upload of the sequence file that might misfire. Well done!

## ENA training material 
* [Webin-CLI Video Guide](https://youtu.be/ChCsqoq-r-Y)
* [ENA quick tour](https://www.ebi.ac.uk/training-beta/online/courses/ena-quick-tour/submitting-data-to-ena/)
* [ENA webinar](https://www.ebi.ac.uk/training/online/course/european-nucleotide-archive-ena-introduction-webin) 
    * [ENA slides only](https://www.ebi.ac.uk/training/online/sites/ebi.ac.uk.training.online/files/ena_webinar_slides_030419.pptx)
* [ReadTheDocs tutorial](https://ena-docs.readthedocs.io/en/latest/)