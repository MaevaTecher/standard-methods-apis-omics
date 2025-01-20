# 11. Data management and open access sharing

Past the excitement from the access to large amounts of sequencing data for numerous honey bee species, populations, individuals, and tissues, researchers may encounter challenges in determining how datasets were obtained. This problem is not inherent to the honey bee community and inconsistencies appear often in many organisms (Gonçalves & Musen, 2019). In the context of honey bee omics research, we have identified two main challenges that hinder comparative studies: 1) the lack of details and access to bioinformatics scripts used and 2) the heterogeneity of metadata associated with open access data. These problems are avoidable with improved practices and standards. Addressing these challenges through standardization and transparency will promote reproducibility and facilitate data comparability and integration.

There are several global and honey bee-specific databases that exist and provide platforms for data submission and search. These databases serve as valuable resources for researchers to access and contribute to the wealth of information available on honey bees. Across the tree of life, the core databases NCBI (National Center for Biotechnology Information), DDBJ (DNA Data Bank of Japan), and ENA (European Nucleotide Archive) are widely recognized as major repositories for biological data. Such databases are now fed by ambitious initiatives that aim to sequence and analyze the genomes of a vast number of species, including those beyond model organisms such as the [Earth Biogenome Project](https://www.earthbiogenome.org/), [Darwin Tree of life](https://www.darwintreeoflife.org/), and [i5K](https://i5k.nal.usda.gov/). These initiatives contribute to the growth of genetic data resources and can indirectly benefit honey bee research.

In addition to the global databases mentioned earlier, several functional genetic databases play important roles in specific model organisms and functional genomics research. While they may not directly contain honey bee datasets, they can still be utilized as proxies for comparative analysis. Some relevant databases include: Flybase, Beetlebase, BUSCO/OrthoDB (Benchmarking Universal Single-Copy Orthologs) and Gene Ontology (GO).

*Apis*-specific databases also exist and have been developed to specifically focus on honey bee microbiome research and provide curated sets of honey bee microbes and associated tools with [Bee-exact](https://github.com/bdaisley/BEExact) and [Holobee](https://data.nal.usda.gov/dataset/holobee-database-v20161). Another example is the [beenome100](http://www.beenome100.org/) project database which serves as a valuable genomic resource and establishes a comprehensive phylogenomic framework for *Apis* genus by aiming at generating reference genomes for 100 U.S. bee pollinators species.

## 11.1. Metadata standardization

While peer-reviewed journals require that any genetic data are shared in open-access, no rigorous quality control of the metadata submitted is ensured. Regardless of the reader's expertise level in submitting genomic data, we recommend following the best practices listed by the journal *Scientific Data* (“Promoting best practice in nucleotide sequence data sharing,” 2020) in submitting metadata to NCBI, DDBJ, ENA, and other databases. This section does not intend to replace the multiple and comprehensive resources available guiding data and metadata submission, and we urge to carefully adhering to these standards (*i.e*., for [NCBI BioProject](https://www.ncbi.nlm.nih.gov/books/NBK54015/?report=reader)).

------------------------------------------------------------------------

**Best practices for BioProjects:**

-   Title should be as explicit and descriptive as intended for publication.

-   Description should include details regarding 1) the project aim, 2) a general overview of the *Apis* species, subspecies, populations, individuals, and sex targeted, 3) the material origin (*e.g.*, tissue specific vs whole body, single individual vs pool), and 4) which sequencing platform and library approach were used.

-   In case the data were released prior to publication, we recommend associating a link to the lab in charge with the institute/unit/team indicated as submitter.

-   Indicate a data usage statement in case of early release to inform users about possible embargo.

-   Contact database curator to give the DOI of the associated published report or paper.

------------------------------------------------------------------------

### 11.1.1. Common problems with *Apis*-related BioProjects

Often, a single study can be associated with a BioProject (*i.e.*, BioProject 1 = X individuals SNPs data, BioProject 2 = Y Transcriptomes) or eventually an umbrella project gathering several related projects (*i.e.*, BioProject UMBRELLA [BioProject 3 = Proteomics data for 100 individuals + and BioProject 2 = Gene expression data for 50 individuals]). One common mistake is the absence of a clear, unique title and description.

Among the 517 BioProjects strictly related to *Apis* honey bee available on NCBI, we found that most did not have associated publications or proper descriptions (Search: "Apis mellifera"[Organism] and manual sorting). This can make it difficult for the reader to know 1) how the data were generated and 2) which institute or team could be contacted to reach out on the origin of the data. Thus, we suggest that researchers follow the subsequent best practices for BioProject submission:11.1.2. Common problems with *Apis*-related BioSamples

From our survey, most of the inconsistency and variability observed in metadata submitted for *Apis* honey bee projects was observed in BioSample (which contains important metadata regarding the source of the sample). A BioSample is essential for cross-scale comparative studies and data mining. Several studies in *A. mellifera* population genetics (see [Section 4.6](https://youneedawiki.com/app/page/1fxIeldyfxt7QFifxFVInw70CVtIGjBVYCzmer3VOPvY?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2)) have generated new genome-wide data but also compared with former studies from a different source in their analysis (Cridland et al., 2017; Dogantzis et al., 2021; P. Shi et al., 2020; Tihelka et al., 2020). Such integrative studies are predicted to increase in the future as they give a broader and global perspective on honey bee evolution and biology.

We found that 16,855 BioSamples related to honey bees and *Apis*-associated environmental organisms (except *Acari* mites and hive insect pests) were registered in public databases. Among them only 60% had attribute fields about the specimen’s sex, and 53% had geographic location details. Aside from incomplete data, in our survey we encountered problems related to variable orthograph even with fields as straight-forward as ‘sex’ attribute (Table 1). While the absence of such data can be understandable and common with historical or third-party sampling, we urge future submissions to include at least the following details for *Apis* standard research.

Table 1. Survey results of BioSample attributes. 

|                                 |               |
|---------------------------------|---------------|
| Orthographs for ‘sex’ attribute | Number of SRA |
| female                          | 3629          |
| femLE [sic]                     | 1             |
| male                            | 1966          |
| MISSING                         | 79            |
| None                            | 6             |
| not applicable                  | 6             |
| not collected                   | 16            |
| not determined                  | 6             |
| pooled male and female          | 418           |
| sterile female                  | 12            |
| worker                          | 22            |
| (no entry)                      | 7629          |

------------------------------------------------------------------------

**Best practices for BioSamples:**

For *Apis* specimen data, use the [invertebrate submission package](http://www.ncbi.nlm.nih.gov/biosample/docs/packages/Invertebrate.1.0/) (<https://www.ncbi.nlm.nih.gov/biosample/docs/packages/Invertebrate.1.0/>) which requires the collection date, the geographical origin, and the tissue used for sequencing

as mandatory attributes.

For *Apis* environmental and metagenomic-transcriptomic data, use the [**MIMS**: metagenome/environmental, host-associated](http://www.ncbi.nlm.nih.gov/biosample/docs/packages/MIMS.me.host-associated.5.0/); version 5.0 package (<https://www.ncbi.nlm.nih.gov/biosample/docs/packages/MIMS.me.host-associated.5.0/>).

In the specific attributes field, we recommend researchers to include the following additional information, although it is not mandatory according to the NCBI submission system.

+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Attribute                                                                                          | Recommendations                                                                                                                                                                                                                                                                                           |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “Breed” or create an additional column “Subspecies”.                                               | When known, include the subspecies or strain level of the honey bee studied (*e.g.*, *Apis mellifera unicolor*, *Apis cerana japonica*, *Apis mellifera* ‘Buckfast’)                                                                                                                                      |
|                                                                                                    |                                                                                                                                                                                                                                                                                                           |
| *Avoid using “isolate” for this purpose and instead use this attribute for the sample name.*       |                                                                                                                                                                                                                                                                                                           |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “biomaterial_provider” and “collected_by”                                                          | Acknowledge the person in charge of the sampling with Name + Affiliation                                                                                                                                                                                                                                  |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “dev_stage”                                                                                        | Indicate if the sample was related to an egg, larvae, pupae or adult bee                                                                                                                                                                                                                                  |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “lat_lon” and “geo_loc_name”                                                                       | Give as many details on the sampling location using geo-coordinates in decimal format, which could be use for spatial studies or to guide future sampling. In some case, the exact geocoordinates can be lost but we recommend to use at least approximate ones (*e.g.,* centroid of a city or locality). |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “treatment”                                                                                        | For transcriptomics and epigenomics studies, the various treatment conditions should be included in the metadata.                                                                                                                                                                                         |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| “host” and “tissue”                                                                                | For metagenomics, metatranscriptomics and microbiomic, include the host species and the origin of the tissue sampled                                                                                                                                                                                      |
+----------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

: Ideally, a supplemental data table should be provided with the sample name, library ID, and all the aforementioned attributes. This would allow future users to cross-check the information with the analysis results, which may not be explicitly stated in the raw data deposited to the database. Examples of such information include population structure assignment, patriline, omic profile, and other relevant details.

------------------------------------------------------------------------

The retroactive correction and update of both BioProject and BioSamples content is often easy and requires the original submitter to contact a curator from the database of initial submission For instance, if you submit your Sequence Read Archive (SRA) data and metadata to DDBJ, you can provide a list of all corrections for each accession to a DDBJ curator. These changes will then be automatically transferred to other databases, such as NCBI, within a short period of time. Since these databases communicate on a daily basis, the changes can be implemented swiftly.
