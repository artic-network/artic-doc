---
title: "LHFV Workshop Tutorial | Installing Workflows"
layout: document
keywords: tutorial
tags: [tutorial, protocol]
summary:
permalink: /tutorials/installing_workflows.html
title_text: "Installing Workflows in Epi2me"
subtitle_text: 
document_name: "installing-workflows-tutorial"
version: v1.0
creation_date: 2026-03-26
last_updated: 2026-03-26
author: Áine O'Toole, Kate Duggan & Daniel Maloney
folder: training
category: tutorial
order: 2
---

<style>
  img {
    max-width: 50%;
    height: auto;
    display: block;
  }
</style>

## Installing Epi2Me

[https://epi2me.nanoporetech.com/epi2me-docs/installation/](https://epi2me.nanoporetech.com/epi2me-docs/installation/)

[EPI2ME](https://labs.epi2me.io/downloads/)

{% include image.html file="epi2me_1.png" prefix=root_url %} <br />

{% include enum.html number='1' content='Today we will run the raccoon-nf pipeline through the [EPI2ME](https://labs.epi2me.io/downloads/) user interface. Please first install the EPI2ME desktop application using the provided link. Follow the setup instructions in the package to install and run EPI2ME.' %}

   {% include image.html file="epi2me_2.png" prefix=root_url %} <br />

{% include enum.html number='2' content='Once you have successfully installed, launch EPI2ME.' %}

   {% include image.html file="epi2me_3.png" prefix=root_url %} <br />

{% include enum.html number='3' content='To access EPI2ME without creating an account, click on the three dots at the bottom of the window, and click "Continue as guest".' %} 

   {% include image.html file="epi2me_4.png" prefix=root_url %} <br />

{% include enum.html number='4' content='When you have successfully launched EPI2ME, you should see the above screen. To install the raccoon-nf pipeline, click to open the "Launch" window in the panel on the left hand side.' %}

   {% include image.html file="epi2me_5.png" prefix=root_url %} <br />

{% include enum.html number='5' content='Click on "Import workflow" in the top right of the window, and then "Import from GitHub".' %}

   {% include image.html file="epi2me_6.png" prefix=root_url %} <br />

{% include enum.html number='6' content='To import the raccoon-nf workflow, paste "https://github.com/Desperate-Dan/raccoon-nf" into the box and click "Download".' %}

   {% include image.html file="epi2me_7.png" prefix=root_url %} <br />

{% include enum.html number='7' content='You should see the above screen if the workflow installed correctly. Click "Open" to launch the workflow.' %}

