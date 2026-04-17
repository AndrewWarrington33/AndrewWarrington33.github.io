---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Andrew Warrington
======  
Boston, MA | [Email](mailto:andrew.warrington.research+cv@gmail.com) | [GitHub](https://github.com/AndrewWarrington33) | [LinkedIn](https://linkedin.com/in/andrew-warrington) | [ORCID](https://orcid.org/0009-0009-4830-5683)

Education
======
* **Oakton Community College** --- *A.S. Computer Science* --- 2025 (Expected)   
* **University of Virginia** --- *B.S. Biology and Psychology* --- 2023   

Work experience
======
**Brigham and Women's Hospital**, Boston, MA --- October 2024 - Present  
*Research Assistant II - [Artificial Intelligence in Medicine (AIM) Lab](https://aim.hms.harvard.edu/)*

* Conducted large-scale genomic and clinical analyses (GWAS, AI-driven clinical phenotyping) across MGB Biobank, radiation oncology, healthy volunteer, and geriatric cohorts.

* Built facial biomarker pipelines using ViT-based transfer learning for AI-derived biomarkers of aging and longevity. FacePhenoAge: fine-tuned FAHR-FaceAge predict PhenoAge, a 9-biomarker laboratory biological age marker, from facial photographs. 

* Developed and deployed the [FaceAge website](https://faceage.bwh.harvard.edu) — a clinical research platform for two IRB-approved studies collecting facial photographs and running ViT-based biological age estimation. *Tech stack:* Flask/Gunicorn, Nginx, Docker (5-container orchestration), Redis/RQ, SQLite. *Features:* e-consent with PDF generation, bcrypt authentication with account lockout and session management, webcam/file photo upload, FaceAge processing and inference pipeline, asynchronous job processing (scheduler → worker pipeline), REDCap and Dropbox integration for HIPAA-compliant data and photo storage. Security hardening: (HTTPS/TLS, Flask-Talisman CSP/HSTS, CSRF protection, rate limiting, input validation and sanitation). All while coordinating simultaneous IRB and IT requirements across MGB infrastructure.

* Engineered multi-stage pipelines for cohort curation, data harmonization, and automated REDCap/Dropbox workflows supporting clinical research.

* Authored and revised IRB protocols, consent forms, and operational documentation; independently managed 7 IRB-approved protocols across MGB and the Dana-Farber/Harvard Cancer Center.

* Initiated and managed recruitment, consent, and administration of screening tools for the interventional Lung-GAP (DFHCC 25-009) trial in geriatric lung cancer patients (NCT06987890).

**Dana-Farber Cancer Institute**, Boston, MA --- July 2023 - October 2024      
*Biospecimen Coordinator - Center for Cancer Genomics (CCG)*

* Directed research study teams in implementing optimal patient sample collection methods from Cross Sectional Interventional Radiology, ensuring strict adherence to IRB protocols in clinical settings over hundreds of collections

* Developed creative solutions and facilitated key discussions during committee meetings to establish sample inventory processes and standard operating procedures for seven CCG projects

* Developed and managed extensive specimen databases for collaborators, providing access to hundreds of fields of data and facilitating new scientific insights

**UVA Psychology Department**, Charlottesville, VA --- August 2022 - December 2022      
*Teaching Assistant - PSYC 2200: The Neural Basis of Behavior*

* Appointed as a teaching assistant for a class of over 100 students in an introductory neuroscience course

* Cooperated to devise complex lesson plans with other TAs and lead instructor for 10 lab sessions

* Created and led exam review sessions for over 100 students

* Directed and graded assignments and student participation for up to 18 students over 1.5-hour lab sessions

**AbbVie**, South San Francisco, CA --- May 2022 - August 2022   
*Experiential Intern - Precision Medicine Pathology*

* Cooperated with a group of 4 scientists during development of Companion Diagnostic Assays for high-stakes AbbVie therapeutics

* Updated and transformed information from thousands of frozen biological samples to assist in company-wide initiative to merge biospecimen data across all AbbVie sites

* Shadowed a board-certified pathologist during QC of hundreds of tissue slides and during the Surgical Pathology Performance Improvement Program offered by the College of American Pathologists (CAP P.I.P.)

* Presented results of internship project to entire AbbVie 2022 intern class in a 10-minute talk

Skills
======
* **Programming & Data Analysis:** Python (pandas, numpy, scikit-learn), Rust, R, C++, PyTorch, CUDA, Docker, Git/GitHub, Linux

* **Web & Systems:** Flask/Gunicorn, Nginx, HTML/CSS, Redis/RQ, SQLite, Docker Compose (multi-container orchestration), dev-stage-prod environment management

* **Security:** authentication, Flask-Talisman (CSP/HSTS), CSRF protection, rate limiting, HTTPS/TLS, session management, input validation

* **Machine Learning:** Vision Transformers (ViT), transfer learning, regression and survival modeling, survival analysis

* **Clinical & Research Data:** REDCap and RPDR integration, data cleaning and visualization, temporal alignment of labs/clinical events, radiation dose (EQD2) harmonization, CBC lab linkage, ICD phenotyping

* **Automation:** REDCap API, Dropbox App Console, reproducible clinical data analysis pipelines, task scheduling and background processing, SMTP email integration

Relevant Coursework
======
* **Oakton Community College:**
Computer Science I, Calculus II, Discrete Mathematics, Data Structures, Calculus III, Introduction to Linear Algebra, Ordinary Differential Equations, Objects and Algorithms
* **UVA:** Machine Learning & Data Mining, Intro Data Science w/ R, Statistics for Biologists, Research Methods and Data Analysis I & II, Calculus I, Physics I & II w/ Lab, Genetics and Molecular Biology, Psychobiology Laboratory

Honors & Awards
======
* **Oakton Community College:**
  * **Joe and Mary Chandler Scholarship Fund 2024 Recipient**

Selected Projects and Presentations
======

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
* **Teaching Assistant** - PSYC2200: The Neural Basis of Behavior
  
Service and Leadership
======
* **Vice President of the Genomics Society @ UVA**
  * I served as the Marketing and Outreach Officer of the Genomics Society from 2020-2022. I served as the Vice President of the organization from 2022-2023. 
* **Director of Activisim and Awareness UAID @ UVA**
  * I joined UAID's chapter at the University of Virginia in the Fall of 2020. In the Fall of 2021 I became the Director of Activism and Awareness for the chapter.
* **Philanthropy Chair for Sigma Nu Beta Chapter**
  * I was elected as the 2021 philanthropy chair for the Beta Chapter of Sigma Nu.
* **Effective Altruism @ UVA** 
  * I was selected for a semester long Effective Altruism Fellowship in the Spring of 2021. I was then trained to be a discussion facilitator for the following semesters.
* **Mental Health Crisis Line Volunteer**
  * Served as a volunteer at HELP Line, a 24/7 confidential telephone hotline serving Albemarle County and UVA students (Open to anyone in the U.S.A.)
  * Completed intensive semester-long training program to develop crisis intervention and active listening skills
  * Provided empathetic, non-judgmental support to callers dealing with various concerns including mental health and relationship issues
  * Connected callers with appropriate long-term resources and professional services
* **UVA Hospital Volunteer**
  * I joined UAID's chapter at the University of Virginia in the Fall of 2020. In the Fall of 2021, I became the Director of Activism and Awareness for the chapter.
* **Habitat for Humanity Charlottesville Volunteer**
  * I volunteered with Habitat for Humanity Charlottesville to help build homes for families in need.

Fitness
======
2025 Marine Corps Marathon Finisher (*50th anniversary*)
* 3:44:44
* 3,959 out of 30,085 Overall
* 3,052 out of 17,758 Male Gender
* 668 out of Male 25-29 Age Group

2024 Washington D.C. Spartan Sprint 5k | 20 Obstacles
* 1:05:19
* 132 out of 1772 Overall
* 113 out of 1106 Gender

2023 Dana-Farber Half-Marathon Finisher
* 1:43:34
* 868 out of 6297 Overall
* 676 out of 2,899 Male Gender
* 96 out of 320 Male 20-24 Age Group

Language
======
* **Spanish**
  * B1 (Intermediate)
