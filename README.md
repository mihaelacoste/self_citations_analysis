## Data Source Disclaimer

The original analysis was performed on proprietary academic data infrastructure. For public sharing and data security:

1.  **Code Functionality:** All SQL queries and Python data processing logic are preserved and fully functional.
2.  **Anonymization:** All BigQuery table paths and project names have been substituted with anonymized placeholders (e.g., `anonymized_project.citation_metrics`). The code cannot be run without replacing these placeholders with valid credentials and table names.

_____________________

## The full methodology and results are published in the corresponding blog post, available here: 

https://fosci.substack.com/p/self-citation-patterns-among-researchers

### Special Thanks go to Leslie McIntosh for the invitation and guidance on this analysis and publication.









Self-citation distribution:

<img width="705" height="192" alt="image" src="https://github.com/user-attachments/assets/eed6279e-c12c-4a2e-b9d9-a7c90b0e9d8f" />

Field of research:

<img width="788" height="750" alt="image" src="https://github.com/user-attachments/assets/23187140-f280-4f53-8a89-cedea7b0ac31" />

Distribution of self-citation threshold by field size:

<img width="1170" height="711" alt="image" src="https://github.com/user-attachments/assets/8a8d33bd-dbe2-46e5-96da-9c5c93b9add9" />

Academic age:

<img width="589" height="345" alt="image" src="https://github.com/user-attachments/assets/d7db8e2f-9f3f-4107-b858-6045777bf009" />

## Methodology:
The data for this analysis were sourced from Dimensions. Our approach focused on isolating a population of active and impactful researchers and then defining and quantifying self-citation at the paper level.
The following criteria were applied to select the eligible research output and researchers:

Document Types: Only research outputs classified as ‘REVIEW_ARTICLE’, ‘RESEARCH_CHAPTER’, ‘RESEARCH_ARTICLE’, or ‘CONFERENCE_PAPER’ were included to focus on core academic contributions.

Reference Threshold: Each included publication was required to have a minimum of 9 references to ensure a substantive engagement with existing literature.

Recent Activity: To identify active researchers, we exclusively considered individuals whose last publication year was 2023 or later.

Publication Volume: We focused on researchers with a minimum of 5 eligible publications within the dataset.

A self-citation, at the paper level, was defined as any cited paper that includes at least one author who is also an author of the citing paper. To illustrate this definition, consider the following examples for a main researcher ‘A’ whose publication has authors ‘A, B’:
- Example 1 (Direct Self-Citation): If researcher A’s publication references R1 (with authors ‘A, X’) and R2 (with authors ‘Y, Z’), this is counted as a self-citation because author ‘A’ from the main publication is also an author of R1.
- Example 2 (Collaborative Self-Citation): If researcher A’s publication references R1 (with authors ‘B, X’) and R2 (with authors ‘Y, Z’), this is also counted as a self-citation because author ‘B’ from the main publication is an author of R1, even though ‘A’ (the first researcher) is not an author of R1.
- Example 3 (Not a Self-Citation): If researcher A’s publication references R1 (with authors ‘Y, X’) and R2 (with authors ‘Y, Z’), this is not a self-citation because neither ‘A’ nor ‘B’ (the authors of the main publication) is listed as an author on any of the referenced papers.
