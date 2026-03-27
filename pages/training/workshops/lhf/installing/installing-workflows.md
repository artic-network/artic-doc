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
folder: workshops
category: workshop
order: 2
---

<style>
  img {
    max-width: 50%;
    height: auto;
    display: block;
  }
</style>

{% capture root_url %}/pages/training/workshops/lhf/installing/images/{% endcapture %}

## Installing Epi2Me

{% include enum.html number='1' content='Download the appropriate installer for your system from the Epi2Me website: <br />
[EPI2ME downloads](https://labs.epi2me.io/downloads/)' %}

{% include image.html file="epi2me_1.png" prefix=root_url %} <br />

Additional instructions for installation can be found here:
[https://epi2me.nanoporetech.com/epi2me-docs/installation/](https://epi2me.nanoporetech.com/epi2me-docs/installation/)

{% include enum.html number='2' content='Once you have successfully installed, launch EPI2ME. To access EPI2ME without creating an account, click on the three dots at the bottom of the window, and click "Continue as guest".' %}


   {% include image.html file="epi2me_2.png" prefix=root_url %} <br />

{% include enum.html number='3' content='When you have successfully launched EPI2ME, you should see the following screen. To install a workflow, click to open the "Launch" window in the panel on the left hand side:' %}

   {% include image.html file="epi2me_4.png" prefix=root_url %} <br />

{% include enum.html number='4' content='Click on "Import workflow" in the top right of the window, and then "Import from GitHub":' %}

   {% include image.html file="epi2me_5.png" prefix=root_url %} <br />

{% include enum.html number='5' content='For this workshop first install amplicon-nf by pasting `https://github.com/artic-network/amplicon-nf` into the box and clicking "Download"' %}

   {% include image.html file="epi2me_6.png" prefix=root_url %} <br />

{% include image.html file="epi2me_7.png" prefix=root_url %} <br />

{% include enum.html number='6' content='You should see the above screen if the workflow installed correctly. Click "Open" to open the workflow. ' %}

{% include image.html file="epi2me_8.png" prefix=root_url %} <br />

At this stage go back and repeat steps 3 - 6 to install another workflow, `raccoon-nf`. Use the following URL to install it: <br />`https://github.com/Desperate-Dan/raccoon-nf`

Your Workflow window should now look like this:

{% include image.html file="epi2me_9.png" prefix=root_url %} <br />

Click on a workflow to open and configure it for launching.
