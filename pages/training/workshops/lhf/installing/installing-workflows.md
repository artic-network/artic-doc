---
title: "LHFV Workshop Tutorial | Installing Workflows"
layout: document
keywords: workshops
tags: [workshops, protocol]
summary:
permalink: /workshops/lhf/installing_workflows.html
title_text: "Installing Workflows in Epi2me"
subtitle_text: 
document_name: "installing-workflows-tutorial"
version: v1.0
creation_date: 2026-03-26
last_updated: 2026-03-26
author: Áine O'Toole, Kate Duggan & Daniel Maloney
folder: lhf
category: tutorial
order: 2
summary: Instructions for installing EPI2ME software and workflows required for the workshop
---

{% capture files_url %}/pages/training/workshops/lhf/installing/files/{% endcapture %}
{% capture root_url %}/pages/training/workshops/lhf/installing/images/{% endcapture %}

## Installing Epi2Me

### 1. Download and install EPI2ME

Download the appropriate installer for your system from the EPI2ME website: <br />

{% include link-out.html url="https://labs.epi2me.io/downloads/" text="EPI2ME downloads: https://labs.epi2me.io/downloads/" image="/pages/training/workshops/lhf/installing/images/epi2me_1.png" max-width="66%" caption="ONT's download page for EPI2ME." %}

Additional instructions for installation can be found here:
{% include link-out.html url="https://epi2me.nanoporetech.com/epi2me-docs/installation/" text="EPI2ME installation instructions" %}

{% include page-break.html %}
### 2. Launch EPI2ME

Once you have successfully installed, launch EPI2ME. To access EPI2ME without creating an account, click on the three dots at the bottom of the window, and click "Continue as guest":

{% include image.html file="epi2me_2.png" prefix=root_url max-width="66%" %}

### 3. Import Workflows

When you have successfully launched EPI2ME, you should see the following screen. To install a workflow, click to open the "Launch" window in the panel on the left hand side: 

{% include image.html file="epi2me_4.png" prefix=root_url max-width="66%" %}

{% include page-break.html %}
Click on "Import workflow" in the top right of the window, and then "Import from GitHub":

{% include image.html file="epi2me_5.png" prefix=root_url max-width="66%" %}

For this workshop first install amplicon-nf by pasting `https://github.com/artic-network/amplicon-nf` into the box and clicking "Download":

{% include image.html file="epi2me_6.png" prefix=root_url max-width="66%" %}

If the workflow installed correctly, should see the following message:

{% include image.html file="epi2me_7.png" prefix=root_url max-width="66%" %}

Click "Open" to open the workflow:

{% include image.html file="epi2me_8.png" prefix=root_url max-width="66%" %}

At this stage go back and repeat steps 3 - 6 to install another workflow, `raccoon-nf`. Use the following URL to install it: <br />`https://github.com/artic-network/raccoon-nf`

Your Workflows window should now look like this:

{% include image.html file="epi2me_9.png" prefix=root_url max-width="66%" %}

Click on a workflow to open and configure it for launching.

{% include page-break.html %}
### 4. Testing the workflows

To test the `amplicon-nf` workflow and download all the required software follow the steps below. The initial downloads can be large but only needs to be done once so testing the workflow before you need it may useful.

Download the following (small) file to use as test data:

{% include file.html file="test_workflow_data.zip" prefix=files_url %}

Uncompressing (expanding) this ZIP file will produce a folder with some folders and files in it:

{% include image.html file="download_file.png" prefix=root_url max-width="66%" %}

<br />

Click on the 'amplicon-nf' workflow to open it:

{% include image.html file="amplicon-nf_1.png" prefix=root_url max-width="66%" %}

Click the 'Launch' button to start an instance of this workflow:

{% include image.html file="amplicon-nf_2.png" prefix=root_url max-width="66%" %}

Then set a few of the input settings of the workflow. Click on "Select a path" and in the file chooser that appears select the `test.csv` file in the `test_workflow_data` folder you downloaded:

{% include image.html file="amplicon-nf_3.png" prefix=root_url max-width="66%" %}

Now scroll down to the section called 'Path containing FASTQ files or barcode directories. Click on "Select a path" and in the file chooser that appears select the `fastq_pass` folder in the in the `preload-amplicon-nf` folder you downloaded:

{% include image.html file="amplicon-nf_4.png" prefix=root_url max-width="66%" %}

Finally, click the "Launch Workflow" button:

{% include image.html file="amplicon-nf_5.png" prefix=root_url max-width="66%" %}

The workflow will start running:

{% include image.html file="amplicon-nf_6.png" prefix=root_url max-width="66%" %}

If everything is setup then it will show that it has completed successfully:

{% include image.html file="amplicon-nf_7.png" prefix=root_url max-width="66%" %}

If you get to this stage then the workflow is installed and ready to run on real data.

### 5. Testing the raccoon-nf

Repeat the steps above to test the **raccoon-nf** workflow.

Click on the 'raccoon-nf' workflow to open it:

{% include image.html file="raccoon-nf_1.png" prefix=root_url max-width="66%" %}

Click the 'Launch' button to start an instance of this workflow. Click on "Select a path" in the "Input sequences in fasta format" setting and in the file chooser that appears select the `test.fasta` file in the `test_workflow_data` folder you downloaded:

{% include image.html file="raccoon-nf_2.png" prefix=root_url max-width="66%" %}

Finally click the "Launch workflow" button and wait until the workflow completes:

{% include image.html file="raccoon-nf_3.png" prefix=root_url max-width="66%" %}

The `raccoon-nf` workflow is now installed and ready to run on real data.
