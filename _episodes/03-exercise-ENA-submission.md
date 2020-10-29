---
title: "Exercise - interactive submission to ENA"
teaching: 10
exercises: 40
questions:
- "I have my datasets, what is the submission process?"
objectives:
- "Explain the steps of submission to European Nucleotide Archive."
- "Do an interactive submission"
keypoints:
- "When in doubt, go to the test submission site: [https://wwwdev.ebi.ac.uk/ena/submit/sra](https://wwwdev.ebi.ac.uk/ena/submit/sra)"
- "The steps of submission process are
1. Sequence file upload to your webin area
2. Register Study
3. Register Samples
4. Submit sequence reads and experiments" 
- "The whole process of submission, from file upload to receiving an accession number takes time.  Do not do this late in the project, when publishers require that you publish datasets before review and deadline is 24 hours."
---
## Do an interactive submission to ENA
* Interactive submission is recommended for registration of your Study and Samples and for small scale Read or Sequence submission.
* Use the test submission site when you want to test and the production site for real submissions:
    * Test site: [https://wwwdev.ebi.ac.uk/ena/submit/sra](https://wwwdev.ebi.ac.uk/ena/submit/sra)
    * Production site: [https://www.ebi.ac.uk/ena/submit/sra](https://www.ebi.ac.uk/ena/submit/sra)
    * *Note: The test service is recreated from the full content of the production service every day at 03.00 GMT/BST. Therefore, any submissions made to the test service will be removed by the following day.*
* Submission steps:
    1. Upload your sequence data
    2. Provide study level information
    3. Choose a MIxS sample checklist
    4. Provide sample metadata
    5. Link the sequencing data to the sample metadata

### File upload
You must upload data files into your private Webin file upload area at EMBL-EBI **before** you can submit the files through the Webin submission service. We will use  *Note: for other options, follow [this link](https://ena-docs.readthedocs.io/en/latest/submit/fileprep/upload.html#file-upload-options)*

1. Launch the Webin File Loader application (Mac users please see further instructions below)

![webin_file_uploader](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/webin_file_uploader.jpg)

2. Enter your Webin username in the `Username` field.
3. Enter your Webin password in the `Password` field.
4. Browse into the local ´Upload Directory` containing the data files you wish to upload using the ... button.
5. Click `okay` to see the list of all the files contained in the selected directory displayed in the Webin File Uploader window
6. Choose `Overwrite` option if you wish to replace any existing files which have been previously uploaded.
7. Choose `Upload Tree` option if you wish to preserve the directory structure when uploading files to the Webin upload area. By default, the files will be uploaded into the root directory of your Webin upload area.
8. Select the files to upload. You can use the `Select All` button to select all the files for upload.
9. Click on the `Upload` button.

**Additional Instructions For Mac Users**

* In order to run the File Uploader application, open your file explorer and go to the directory where the `WebinUploader.jnlp` file has been saved.

* While pressing the <kbd>Ctrl</kbd> button, select the WebinUploader.jnlp file then select the `Open` option.

* The following dialog will now be displayed:

![mac_webin_file_upload](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/mac_webin_file_upload.png)

* Now select the `Open` button. This will launch the application.

### New submission
1. Go to the test service: [https://wwwdev.ebi.ac.uk/ena/submit/sra](https://wwwdev.ebi.ac.uk/ena/submit/sra) and log in with your Webin username and password. 
2. Go to the `New Submission` tab. Each of the options displayed will lead you to interactive web forms that guide you through the submission of these objects. Interactive submission is recommended for registration of your Study and Samples.
![new_submission_1-2-3](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/new_submission_1-2-3.jpg)
3. Use the [Register study (project)](https://ena-docs.readthedocs.io/en/latest/submit/study/interactive.html) option to register new studies.
![select_register_study](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/select_register_study.jpg)
* **Title**: VEGFR2 Y949F mutation
* **Abstract**: RNA sequencing of lung tissue from transgenic mice in order to investigate the effect of a single tyrosine to phenylalanine exchange in the endothelial receptor VEGFR2 at position Y949.
* Click on **Next**
> ## Solution
> ![register_study](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/register_study.jpg)
{: .solution}
4. Use the [Register samples](https://ena-docs.readthedocs.io/en/latest/submit/samples/interactive.html) option to register new samples.
![select_register_sample](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/select_register_sample.jpg)
* Select a checklist, for our purpose the `Other Checklists`> `ENA default sample checklist` is suitable.
* Click on **Next**
> ## Solution
> ![select_checklist](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/select_checklist.jpg)
{: .solution}
* Add two fields from **Part and developmental stage of organism**: `dev_stage` and `tissue_type`.
* Click on **Next**
> ## Solution
> ![add_fields](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/add_fields.jpg)
{: .solution}
* Fill in all information that is in common for all samples
    * Organism Details - Search for `mouse` and choose `Mus musculus` in the search result.
    * Part and developmental stage of organism - `adult` as `dev_stage` and `lung` as `tissue_type`
* Click on **Next**
> ## Solution
> ![template_all_samples](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/template_all_samples.jpg)
{: .solution}
* Click on `+ Add` button and fill the Basic details
    * `Unique name` - a_wt
    * `Title`- Sample a wildtype
* Click on **Submit**
> ## Solution
> ![template_sample_a](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/template_sample_a.jpg)
{: .solution}
> ## Note
> We will only register one sample, but typically there are many samples and it can be wise to download a template and fill it in e.g. Excel.
{: .callout}
5. Use the [Submit sequence reads and experiments](https://ena-docs.readthedocs.io/en/latest/submit/reads/interactive.html) option to submit sequence reads with associated experimental information.
![submit_reads](https://nbisweden.github.io/module-repository-submission-dm-practices/fig/select_submit_reads.jpg)
* Select your Study accession (typically starting with PRJEB) and click on **Next**
* Since we already have submitted our Sample, click on **Skip** in the next window
* Fill in the Run information
    * Click on BAM as file format
    * Sample reference - a_wt
    * Instrument Model - Illumina HiSeq 2500
    * Library Source - TRANSCRIPTOMIC
    * Library Selection - other
    * Library Strategy - RNA-Seq
    * Library Layout - SINGLE
    * File Name - a_wt.bam
    * MD5 checksum - 9a7183503166cf772492c7d6581f3b72
* Click **Submit**

## Files to submit
This sequence file (.bam format) needs to be downloaded previous to exercise 
A_Wt https://www.ebi.ac.uk/arrayexpress/files/E-MTAB-9163/E-MTAB-9163.up_201_1.bam 


## Reference material 
https://www.ebi.ac.uk/training-beta/online/courses/ena-quick-tour/submitting-data-to-ena/

Slides and webinar: https://www.ebi.ac.uk/training/online/course/european-nucleotide-archive-ena-introduction-webin 

Slides only: https://www.ebi.ac.uk/training/online/sites/ebi.ac.uk.training.online/files/ena_webinar_slides_030419.pptx

ReadTheDocs tutorials: https://ena-docs.readthedocs.io/en/latest/, https://ena-docs.readthedocs.io/en/latest/submit/general-guide.html 