# 11. Data management and open access sharing

## 11.2. Sharing pipelines and scripts

The burst and diversification in the development of software, **R** packages, pipeline and servers to analyze omics data can quickly lead users to go down a bioinformatic rabbit hole to make the “best” choice. Additionally, the frequent emergence of comparative studies promoting new tools adds to the difficulty of decision-making. In this chapter, we have proposed up-to-date and efficient standard pipelines to guide users in their methodological workflows. However, we acknowledge that these pipelines may require future revisions, similar to how the present chapter updates information from Evans et al. (2013). We aim to provide a valuable resource that evolves alongside advancements in the field.

As progress is made and new analytical workflows are adopted, we invite the honey bee research community to contribute to the data processing standardization by sharing their bioinformatics methods and custom scripts. While sharing sequencing data is mandatory in peer-reviewed journals, the same level of detail is often not required for downstream analysis. Minimal descriptions are often given in the “Material and Methods” sections regarding parameters for each software or script function. Depending on the journal's requirements, it may be necessary to share analysis output data (e.g., VCF files, LFMM, FASTA) and scripts through external repositories associated with a DOI.

Noteworthy initiatives, such as the ***SeqApiPop*** population genomics study, have inspired changes by publishing detailed codes on collaborative platforms like GitHub (github.com/avignal5/SeqApiPop) alongside their results (Wragg et al., 2021). Similar initiatives using interactive **R** and shell markdowns have been carried out for honey bee microbiome (Kowallik & Mikheyev, 2021; Liberti et al., 2022) and transcriptomics studies (Holman et al., 2019; Warner et al., 2019). In addition to enabling reproducibility and standardization, we advocate that open access to the code scripts (default and personalized) serves as a valuable teaching tool, particularly tailored to honey bees. To facilitate the growth of such resources, we recommend the following best practices:

------------------------------------------------------------------------

**Best practices for sharing pipelines and scripts:**

-   Whole genome sequencing and population genomics studies should strive to make their data freely available through international open-access repository such as Dryad or Zenodo.

    Content: VCF file, Demographic analysis, FASTA alignments

-   **Custom scripts** (bash, Python, awk) and **pipelines** created with Workflow Management Systems (such as Snakemake, Nextflow, Galaxy) should be made freely accessible to a cloud-based platform with version control, such as GitHub (or alternatives: GitLab, Bitbucket, SourceForge, *etc.*) or Wiki.

    Content: Markdown, codes, notes, input files (small sizes)

-   State clearly in publication the source and link to data and code availabilities

------------------------------------------------------------------------

When selecting a community-curated pipeline, users should consider the following: 1) How often has this pipeline been cited and used? 2) Does the closed/open issues ratio or forum activity indicate strong developer technical support? 3) How frequently is the pipeline updated (consider the dates and number of releases)? 4) Is there an active user community providing support? Additionally, with the rise of package manager such as **Conda** or containerization technologies like **Docker** and **Singularity**, it’s important to consider if the pipeline is available in a containerized format, as this can significantly improve the reproducibility and ease of its usage across different computing environments.
