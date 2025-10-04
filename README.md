# MetsExtract
Metastasis extraction from EHR notes using LLMs.

This study aims to predict the presence of metastasis and the location of metastasis in NSCLC patients based on radiology reports. 
1) We selected the GatorTron model developed by researchers at the University of Florida to fine-tune for our metastasis-focused prediction tasks. We accessed the GatorTron-Base model through HuggingFace
2) We gathered de-identified discharge notes (n=213) from the MIMIC-III database, which already contained annotations on which notes indicated "advanced cancer" status for the patient, which we used this as a proxy for metastasis. Additionally, we manually annotated each note for presence and location of metastasis.
3) We used MedspaCy sectionizer and sentence-by-sentence filtering to filter through each note. For notes with mentions of metastasis, we only kept sentences with mention of metastasis or other related terms. For notes without mentions of metastasis, we kept only selected sections of the text.
4) We used the filtered MIMIC-III notes to fine-tune the GatorTron model by conducting two different sequence classification tasks: one for identifying the presence of metastasis and another for identifying the location of metastasis.
5) We then applied this fine-tuned model on the cohort of NSCLC radiology notes at Emory to obtain predictions on metastasis presence and location.
