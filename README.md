# Metastasis extraction from EHR notes using LLMs.

This study aims to predict the presence of metastasis and the presence of CNS metastasis, respectivelt in NSCLC patients based on radiology reports. 
1) We selected the GatorTron model developed by researchers at the University of Florida to fine-tune for our metastasis-focused prediction tasks. We accessed the GatorTron-Base model through HuggingFace
2) We gathered a cohort of 643 radiology notes from the Winship Cancer Institute. These notes corresponded to 22 NSCLC unique patients.
3) We created an NLP pipeline leveraging the MedspaCy sectionizer and sentence-by-sentence filtering to filter through each note. For notes with mentions metastasis-related keywords (as specified in a curated text file), we filtered to keep only the sentences containing these keywords. For notes without mentions the defined keywords, selected sections of the notes were kept.
4) The filtered notes were then manually annotated by the team of researchers. 2 independent reviewers evaluated the notes and annotated them for metastasis presence and CNS metastasis presence, respectively. Disagreements between reviewers were discussed, and a professional clinician was consulted to support the annotations.
5) The annotated notes were used to conduct a 5-fold cross-validation to tune the GatorTron model. Each fold was then ensembled to conduct validation on a new, unseen cohort of radiology notes.
6) A new set of notes were inputted, filtered using the aforementioned NLP pipeline.
7) The fine-tuned, ensembled model was then applied to the new, unseen cohort of radiology notes to obtain predictions on metastasis presence abd CNS metastasis presence for each note.

Immediate Next Step
1) The unseen cohort of radiology notes will be manually annotated by the reviewers to evaluate the acuracy, precision, recall, and f1 of the model on unseen data.
