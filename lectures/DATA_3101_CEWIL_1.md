CEWIL 1
================

# Introduction to Open Journal Systems, Metadata, and XML

### CEWIL Project Context

CEWIL = Co-operative Education and Work-Integrated Learning

#### Applicants:

Dr. Steve Geier (STEM Librarian and CHEM/BIOC 3991 Research and
Communication Lecturer)

Elizabeth Stregger (Data & Digital Services Librarian and DATA 3101 Data
Acquisition and Organization Lecturer)

#### Partner:

[*Theory and Application of Categories*](http://www.tac.mta.ca/tac/), a
math journal hosted at MtA since 1995. Dr. Geoffrey Cruttwell is the
Managing Editor.

#### Background:

Dr. Cruttwell reached out to the Libraries & Archives in 2021 to find
out if we could provide archiving (in paper) or preservation (digital)
of this journal. At this point I started to think about how we could
better support this journal (and others) through publishing services.
Over the years, we’ve also had questions from the editors
[ATLIS](https://atlis.wordpress.com/archives/) and [Material Culture
Review / Revue de la culture
materielle](https://journals.lib.unb.ca/index.php/MCR/index).

There are three guest lectures that set the scene for our project this
term:

- Dr. Vincent Lariviere: [Open Science: Key issues for
  action](https://mountallison-my.sharepoint.com/:v:/r/personal/sgeier_mta_ca/Documents/Recordings/Guest%20Talk%20at%20Mount%20Allison%20University-20241022_180017-Meeting%20Recording.mp4?csf=1&web=1&e=kfAlmY&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)

- Dr. John Aspler: [Why persistent identifiers matter: ORCID iDs and
  DOIs in the Canadian
  Context](https://mountallison-my.sharepoint.com/:v:/g/personal/sgeier_mta_ca/ESsKDXlD5BBAp9sa5qtOtpwBnwefo_eJUEiakDGGe7C7Xw?e=rf4sNe&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)

- Dr. Geoff Cruttwell: [*TAC:* History and
  workflows](https://mountallison-my.sharepoint.com/:v:/r/personal/sgeier_mta_ca/Documents/Recordings/Research%20and%20Communication%20Class-20241024_113254-Meeting%20Recording.mp4?csf=1&web=1&e=0tga0C&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D)

**The project:**

Develop and compare workflows for transforming the metadata on the *TAC*
website to the format required for transfer or upload to Open Journal
Systems:

- Human metadata work (CHEM/BIOC 3991): Add content to the journal using
  the [Quick Submit Plugin](https://docs.pkp.sfu.ca/quicksubmit/en/)

- AI-assisted work (CHEM/BIOC 3991 & DATA 3101): Experiment with using
  [GPT Teams](https://team-gpt.com/ai-use-cases/data-science/) to get
  the output we need

- Webscraping in R (DATA 3101): Scrape *TAC* website, transform data as
  required, output in XML

**What the grant covers:**

- Membership in CrossRef (one of the agencies that can register DOIs)

- DOI costs for registration of existing items

- GPT Teams accounts for instructor teams and students in both courses

- Guest lectures and snacks

- Student stipends

#### Other contributors:

Computing Services and Kristian Strickland, the IT Specialist in the
library, will be setting up an Open Journal Systems server.

Until this is set up, we can use the [demo
OJS](https://pkp.sfu.ca/software/ojs/demo/) for testing, which is
over-written overnight.

### Open Journal Systems (OJS)

- Very widely used free and open source project used for over 44,000
  journals

- Extensive [user guide](https://docs.pkp.sfu.ca/) (including editor
  workflows, [metadata best
  practices](https://docs.pkp.sfu.ca/metadata-practices/en/), plugin
  information, and lots of help) and [technical
  documentation](https://docs.pkp.sfu.ca/dev/) for system administrators

- Integrates with persistent identifiers such as
  [DOI](https://www.doi.org/), [ORCID](https://orcid.org/), and
  [ROR](https://ror.org/)

- [PKP Preservation Network](https://pkp.sfu.ca/pkp-pn/): A lots of
  copies keep stuff safe (LOCKSS) dark archive for preservation and
  long-term access. This is turned on through a plug in in OJS. Every
  new issue is harvested. Access through the PKP Preservation Network is
  typically triggered through a cessation of publication.

- Overall, our goal is to keep MtA edited journals free, make them
  easier to find, connect them to the scholarly infrastructure, and
  preserve them for the future.

### Research and Communication Class

Today I’ll work through an example of creating a new issue of *TAC* in
the test journal and adding an article using the Quick Submit Plugin.
Then I’ll export the example using the Native XML Plugin for the DATA
3101 class to use for learning about XML.

In Thursday’s class, you’ll work on doing this for another article. Then
you’ll review someone else’s work. We’ll start a list of questions that
need to be answered for this workflow.

### Data Acquisition and Organization Class

In this project, we’re acquiring textual data and cleaning and
transforming it to meet a different standard. The textual data is in
HTML and we need to transform it into the XML schema used by OJS.

First, let’s look at the source code for
[TAC](http://www.tac.mta.ca/tac/) (look at both the journal homepage and
one specific article) The website meets the [HTML 4.01 Transitional
Document Type
Definition](https://www.w3.org/TR/html4/sgml/loosedtd.html).

Our goal is to transform this data so that it conforms to the schema for
the [Native XML
Plugin](https://docs.pkp.sfu.ca/admin-guide/en/data-import-and-export#create-a-native-xml-file-for-import)
for Open Journal Systems.

Today we’ll learn (or do some review) about HTML and XML.

HTML (**H**yper **T**ext **M**arkup **L**anguage) used for website
display

XML (e**X**tensible **M**arkup **L**anguage) used for exchange and
transfer of data

[W3 Schools HTML Tutorial](https://www.w3schools.com/html/default.asp)

[W3 Schools XML Tutorial](https://www.w3schools.com/xml/default.asp)

[Mozilla mdn web docs:
HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)

[Mozilla mdn web docs:
XML](https://developer.mozilla.org/en-US/docs/Web/XML/XML_introduction)

What are some of the similarities and differences?

#### Discussion:

We can keep a running list of questions and issues to be solved.

- How does PDF encoding work in the Native XML plugin?

- How will we extract information from within the PDF (author
  affiliation, for example?)

- Question for Dr. Cruttwell: Is there a primary / corresponding author?

### Additional Resources:

Working with text as data: Constellate classes available live or
asynchronously

[Introduction to Large Language
Models](https://constellate.org/events/introduction-to-large-language-models)

[Automated Text
Classification](https://constellate.org/events/automated-text-classification)
