# 5. Epigenomics

## 5.3. Epitranscriptomics: RNA methylation of m6A

Besides the chemical modifications on the DNA, RNA molecules can also undergo more than 100 different dynamic chemical modifications that impact gene expression (Roundtree et al., 2017; Sánchez-Vásquez et al., 2018). The study of RNA methylation so far has mainly focused on the N6-methyladenosine (m6A) modification, which occurs in mRNAs of eukaryotes and represents about 80% of all RNA methylation in the honey bees (Wang et al., 2021). In honey bees, recent discoveries have linked m6A methylation to larval development and caste differentiation, highlighting its significance in *Apis* biology (Bataglia et al., 2021; Wang et al., 2021). Epitranscriptomics is the field that focuses on studying all types of mRNA mRNA modifications, including m6A. The protocol below describes how to quantify total m6A methylation across all transcripts, but more advanced methods must be used to actually identify the sites of methylation.

### 5.3.1. Considerations for testing global RNA methylation of m6A

-   This test requires a precise quantity of RNA input; therefore, it is crucial to have the equipment to quantify the RNA concentration in your RNA extraction sample. Nanodrop spectrophotometers or Qubit fluorometers can both provide accurate concentration information about your sample, but the latter is recommended for accuracy.

-   The EpiQuik m6A RNA Methylation Quantification Kit (*EpiGentek*) can be used to quantify total m6A methylation globally across a complete RNA sample. The range of the RNA quantity is 100 ng to 300 ng. See Evans *et al.* (2013) for sample handling and RNA extraction protocols.

### 5.3.2. Materials

-   Large equipment: Microplate reader capable of reading absorbance at 450 nm, 37 °C incubator
-   Kits: EpiQuik m6A RNA Methylation Quantification Kit (*EpiGentek*) including negative and positive RNA controls, capture antibody, detection antibody, wash buffer, binding solution, enhancer solution, developer solution, stop solution, standard control
-   8-well assay strips
-   Distilled water
-   1x TE buffer with pH 7.5 -8.0
-   Adjustable pipette
-   Aerosol-resistant filtered pipette tips
-   96 well plates
-   1.5 ml microcentrifuge tubes
-   Plate sealing film or parafilm M

### 5.3.3. Procedure

1.  Follow the kit manufacturer’s instructions for RNA binding, antibody binding, and RNA quantification.

2.  After color development, measure absorbance at 450 nm.

    1.  For relative quantification, the percentage of m6A in total RNA can be calculated based on the average OD450 of negative control, average OD450 of positive control, average OD450 of sample, the amount of input sample RNA in ng, and the amount of input positive control in ng.

    2.  For absolute quantification, a standard curve can be generated based on the m6A standard controls (0.01, 0.02, 0.05, 0.1, 0.2, and 0.5 ng/ul). With the standard curve, the amount of m6A in the total RNA sample can be calculated using sample OD minus negative control OD, then divided by the slope. The proportion of m6A in the samples can be calculated using m6A amount in ng divided by input quantity (for example 200 ng).

### 5.3.4. Identifying methylation sites

Although global m6A methylation is valuable for assessing large-scale methylation states, it is beneficial to understand which specific residues are modified on a transcript. Most RNA extraction techniques retain the methylation state on the mRNA transcripts, and there are several ways that the m6A sites may be identified. m6A-seq uses ribose-sensitive nuclease digestion and high-throughput sequencing (Dominissini et al., 2013). MeRIP-seq (Meng et al., 2014) is another approach which uses m6A-specific antibodies to pull down m6A-containing RNAs and then sequences them.

A final option is Nanopore MinION sequencing. Using this technique, you can glean which specific RNA transcripts have m6A methylation as well as which residues are modified. Nanopore MinION direct RNA sequencing (dRNA-seq) provides long reads (10,000–30,000 base fragments being common) and, in some cases, can provide reads of entire transcripts. The advantage of dRNA-seq is that one sequencing procedure can include information of both transcriptome and m6A methylome modifications of RNA. See [Section 6.2](https://maevatecher.github.io/standard-methods-apis-omics/Part_6_2/) for more information on direct RNA sequencing.

### 5.3.5. Software recommendations

For m6A RNA methylation from the Nanopore dRNA-seq data, one new tool for identifying differential RNA modifications is called **xPore** (Pratanwanich et al., 2021). **xPore** uses a machine learning-based approach to predict the presence and location of RNA modifications, including m6A, within the dRNA-seq reads. It also allows for the quantification of modification levels, and it can also be used to identify differentially modified sites between different samples or conditions. **xPore**'s ability to handle long read lengths of direct-RNA sequencing data allows for accurate detection of m6A modifications in introns and exons, as well as in regions spanning multiple exons, resulting in higher resolution and more comprehensive coverage of m6A sites. It allows for high-resolution and comprehensive detection of m6A modifications, which can help to improve our understanding of the role of m6A in regulating gene expression.

One of the main challenges in the analysis of m6A site data is distinguishing true m6A modifications from sequencing noise. To address this, many tools use a threshold-based approach to call m6A sites, which involves setting a threshold for the minimum number of reads or the minimum proportion of methylated reads required to call a site as methylated. The choice of threshold will depend on the sequencing depth and the desired level of specificity and sensitivity. Similar to other transcriptomic analyses, multiple hypothesis testing must be accounted for (by using a Benjamini-Hochberg correction, for example).
