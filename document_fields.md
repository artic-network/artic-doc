## Front-matter fields in ARTIC documents
           
### Resource pages
A description of the various fields that can be put in the Jekyll block at the top of a document. The following are used in resource description pages (e.g., here the measles virus resources page). These pages are for organising documents on the website and are not intended for printing.

`title: MeV (Measles virus)`
: This is the title of the page - will appear at the top of the browser and as a title on the page.

`tname: MeV<br>(Measles virus)`
: This is the title text that will be used in a set of tiles on the resources page. It will usually be two lines.

`icon: /images/viruses/mev_icon.svg`
: This is the icon that will be used in a set of tiles on the resources page

`keywords: resources`
: 

`summary: A collection of resources for whole genome sequencing and analysis of Measles virus (MeV)`
: A summary paragraph that will go at the top of the page.

`image: /images/viruses/mev.png`
: An image that will go next to the summary paragraph (optional)

`sidebar: artic_sidebar`
: Which sidebar to use (at the moment `artic_sidebar` is the only one and is default - use `false` to hide the sidebar).

`permalink: /viruses/mev`
: The URL that will be used for this page. For resource pages this can be just the folder without an extension. For documents this should have the `.html` extension.          

`folder: viruses`
: The notional folder that the document would go in. This is used to make collections and for listing documents in the collection. 

`tags: [resources, viruses]`
: Tags are used to show collections of document and pages. Not currently used but may be in future.


### Documents
These are individual documents that follow a particular layout and are intended to be printed or turned into PDFs for distribution.

`title: "Measles virus sequencing"`
: This is the title of the document - will appear at the top of the browser.

`keywords: resources`
: Can't remember what this is used for - probably for search.

`layout: document`
: This layout is specifically for printable documents

`tags: [resources, viruses]`
: Tags are used to show collections of document and pages. Not currently used but may be in future.

`folder: mev`
: What folder this document is part of - i.e., a collection. Used by the resource pages to show documents in the collection.
            
`category: guide`
: What type of document this is - which will be used to categorise it under a subheading. Currently we use things like `guide`, `sop`, `setup`, `cli` and `epi2me` but it depends on the resource page that is hosting it.

`order: 1`
: The order that the document will be listed in the category.

`title_text: "Measles virus sequencing"`
: This is used as the main title at the top of the document. 

`subtitle_text: "A primer on measles virus genomic epidemiology and why we do it"`
: A subtitle that will appear after the title

`document_name: "ARTIC-MeV-guide"`
: The name of the document in the info box

`version: v1.0.0`
: The version number of the document. Update as appropriate.

`creation_date: 2024-08-20`
: When the document was created. This doesn't change.

`last_updated: 2024-08-20`
: When the document was last updated. When you update a document, update this.

`forked_from: <document name>`
: If a document is a copy and edit from another document then this can be specified here.

`author: ARTIC team`
: The author or authors of the document

`citation:`
: A citation in text format to a publication using a DOI or similar. If the document has been published.
