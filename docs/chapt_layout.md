# Abstract

# Keywords

# Funding details

# Disclosure statement

# 1.  The ‘omics revolution in Apis: More data than meets the eye

# 2.  Sample management

# 3.  Genome sequencing

## 3.1. Introduction

## 3.2. Genome sequencing technologies

### 3.2.1. Sanger sequencing

### 3.2.2. Next generation sequencing

### 3.2.3. Long-read sequencing

## 3.3. The reference genome

### 3.3.1. Assembling the reference genome

#### 3.3.1.1. Hi-C chromosome conformation capture

#### 3.3.1.2. DNA source selection

### 3.3.2. Annotating the reference genome

### 3.3.3. High molecular weight DNA extraction

## 3.4. Small and large variant detection

### 3.4.1. RAD-seq

## 3.5. Sequencing museum specimens

### 3.5.1. Considerations

### 3.5.2. Materials

### 3.5.3. Procedure

#### 3.5.3.1. Preparation and lysis

#### 3.5.3.2. DNA extraction

#### 3.5.3.3. Precipitation

#### 3.5.3.4. Washing

#### 3.5.3.5. Final solubilization

### 3.5.4. Sequencing of museum and ancient genomes

### 3.5.5. Guidance on the data analysis methods

### 3.5.6. Applications and limitations

# 4.  Whole-genome population and association studies

## 4.1. Introduction

## 4.2. Ploidy and sampling considerations

### 4.2.1. Individual sampling

### 4.2.2. Pooled sampling

#### 4.2.2.1. Groups of workers

#### 4.2.2.2. Groups of drones

## 4.3. SNP and indel detection

### 4.3.1. Mapping reads with BWA-MEM: From FASTQ files to BAM files

### 4.3.2. Marking duplicate reads with Picard

### 4.3.3. Base quality score recalibration (BQSR) with GATK

### 4.3.4. Calling variants with GATK

### 4.3.5. Combining all samples and genotypes with GATK

### 4.3.6. Filtering variants with GATK: Technical filters

### 4.3.7. Filtering variants with VCFtools: Data quality

### 4.3.8. Genotype phasing

### 4.3.9. SNP annotation with SnpEff

### 4.3.10. SNP analysis by sequencing pooled samples

#### 4.3.10.1. From FASTQ files to BAM files

#### 4.3.10.2. SNP selection and pileup files

#### 4.3.10.3. Counting reads per allele with PoPoolation

## 4.4. Comparing whole genomes

### 4.4.1. Conducting a pairwise genome comparison with LAST

## 4.5. Genome-wide association studies

### 4.5.1. Considerations for phenotypic data

### 4.5.2. Considerations for sample selection

#### 4.5.2.1. Power analysis

### 4.5.3. Materials

#### 4.5.3.1. Computational resources

#### 4.5.3.2. Genotypic and phenotypic data

### 4.5.4. Methods

#### 4.5.4.1. Preparation of phenotypic data

#### 4.5.4.2. Preparation of genotypic data

#### 4.5.4.3. Performing GWAS: Methods and software

#### 4.5.4.4. Detecting signatures of selection

### 4.5.5. Sources of variation

### 4.5.6. Quality control and data interpretation

### 4.5.7. Applications and limitations

## 4.6. Population genomics: Experimental design

### 4.6.1. Sampling strategy

#### 4.6.1.1. Sample sizes of individuals and markers

#### 4.6.1.2. Sample breadth

#### 4.6.1.3. Sampling design

#### 4.6.1.4. Sampling workers versus drones

#### 4.6.1.5. Sampling a single individual versus multiple individuals per colony

## 4.7. Population genomics: Filtering and summary statistics using PLINK

### 4.7.1. Download and installation

### 4.7.2. Input format and conversion

#### 4.7.2.1. Variant call format (VCF)

#### 4.7.2.2. PLINK 1 binary format (.bim)

#### 4.7.2.3. Regular PLINK text files

#### 4.7.2.4. Filtering and handling missing data

#### 4.7.2.5. Computing and filtering based on allele frequency

#### 4.7.2.6. Computing differentiation indices: Wright's FST

#### 4.7.2.7. Estimating linkage disequilibrium

## 4.8. Population genomics: Inferring population structure using ADMIXTURE

### 4.8.1. Download and installation

### 4.8.2. Input files

### 4.8.3. Methods

## 4.9. Landscape genomics: An example using LFMM

### 4.9.1. Materials

### 4.9.2. Methods

## 4.10. Applying population genomics to conservation: Reduced SNP analysis

### 4.10.1. Materials

### 4.10.2. Methods

# 5.  Epigenomics

## 5.1. Introduction

## 5.2. DNA methylation

### 5.2.1. Bisulfite-seq

#### 5.2.1.1. Considerations

#### 5.2.1.2. Materials

#### 5.2.1.3. Methods

### 5.2.2. Methylated DNA immunoprecipitation-sequencing (MeDIP-seq)

#### 5.2.2.1. Considerations

#### 5.2.2.2. Materials

#### 5.2.2.3. Methods

### 5.2.3. Data processing and analysis

#### 5.2.3.1. Software recommendations

#### 5.2.3.2. Data repository

#### 5.2.3.3. Statistical analysis

## 5.3. Epitranscriptomics: RNA methylation of m6A

### 5.3.1. Considerations for testing global RNA methylation of m6A

### 5.3.2. Materials

### 5.3.3. Procedure

### 5.3.4. Identifying methylation sites

### 5.3.5. Software recommendations

## 5.4. Chromatin organization and histone modifications

### 5.4.1. Chromatin immunoprecipitation sequencing and transcription factor binding motifs

### 5.4.2. Hi-C & chromatin conformation

### 5.4.3. Chromatin accessibility and transcriptional factor motifs

### 5.4.4. Detecting histone modifications by mass spectrometry

## 5.5. Applications and limitations

# 6.  Transcriptomics

## 6.1. Introduction

## 6.2. Sequencing technologies

### 6.2.1. Considerations

### 6.2.2. Illumina sequencing (short reads)

### 6.2.3. Third generation sequencing (long reads)

#### 6.2.3.1. Considerations for choosing a long-read platform

## 6.3. Single-cell transcriptomics

### 6.3.1. Considerations

### 6.3.2. Materials

### 6.3.3. Sample preparation procedure for single-cell sequencing

## 6.4. Data handling and analysis

### 6.4.1. RNA-seq and differentially expressed genes (DEGs)

### 6.4.2. Gene network analysis

### 6.4.3. Single-cell transcriptomics

#### 6.4.3.1. 10x Genomics specific software

#### 6.4.3.2. Third party software

## 6.5. Applications and limitations

# 7.  Functional genomics and xenobiotic treatment

## 7.1. Introduction

## 7.2. CRISPR

### 7.2.1. Considerations

### 7.2.2. Materials

### 7.2.3. Methods for CRISPR/Cas9 gene editing of embryos

#### 7.2.3.1. Generating Cas9 protein.

#### 7.2.3.2. Generating sgRNA

#### 7.2.3.3. Ribonucleoprotein assembly

#### 7.2.3.4. Egg collection and microinjection

## 7.3. RNA interference

### 7.3.1. RNAi considerations

### 7.3.2. Methods for nanoparticle-mediated RNAi

#### 7.3.2.1. Materials

## 7.4. Xenobiotic treatment

### 7.4.1 Xenobiotic treatment considerations

### 7.4.2. Materials

### 7.4.3 Procedure

#### 7.4.3.1 Thorax application

#### 7.4.3.2. Injection

#### 7.4.3.3. Feeding individual bees

#### 7.4.3.4. Flight cage feeding

## 7.5. Applications and limitations

# 8.  Proteomics

## 8.1. Introduction

## 8.2. Standard methods for shot-gun proteomics sample preparation

### 8.2.1. Considerations

#### 8.2.1.1. General

#### 8.2.1.2. Sample handling

#### 8.2.1.3. Reagent handling

### 8.2.2. Materials

### 8.2.3. Proteomics methods

#### 8.2.3.1. Lysis and precipitation

#### 8.2.3.2. Solubilization and digestion

#### 8.2.3.3. Peptide desalting and resuspension

## 8.3. Liquid chromatography and mass spectrometry

## 8.4. Proteomics data processing

### 8.4.1. Software recommendations

#### 8.4.1.1. MaxQuant and DIA-NN search parameters

#### 8.4.1.2. Choosing an appropriate protein database

#### 8.4.1.3 Statistical analysis

## 8.5. Applications and limitations

# 9.  Metabolomics

## 9.1. Introduction

## 9.2. Sample preparation for metabolomics

### 9.2.1. Considerations

#### 9.2.1.1 General

#### 9.2.1.2. Sample handling

#### 9.2.1.3. Reagent handling

#### 9.2.2. Materials

### 9.2.3. Metabolomics methods

#### 9.2.3.1. Sample homogenization

#### 9.2.3.2. Extraction

## 9.3. Chromatography and mass spectrometry

## 9.4. Metabolomics data processing

## 9.5. Metabolomics applications and limitations

# 10. Microbiome analysis

## 10.1. Introduction

## 10.2. Sampling and DNA extraction

### 10.2.1. Considerations

#### 10.2.1.1. General

#### 10.2.1.2. Tissue sample handling

#### 10.2.1.3. Hive material sample handling

### 10.2.2. Protocol for tissue samples

#### 10.2.2.1. Materials

#### 10.2.2.2. Dissection methods

#### 10.2.2.3. DNA extraction methods

### 10.2.3. Protocol for sampling hive materials

#### 10.2.3.1. Materials

#### 10.2.3.2. Methods for bee bread sampling and DNA extraction

10.2.3.3. Methods for hive entrance sampling and DNA extraction

## 10.3. Amplicon sequencing

### 10.3.1. Considerations

### 10.3.2. Materials for amplicon sequencing

### 10.3.3. Methods for amplicon sequencing

## 10.4. Microbiome data analysis

### 10.4.1. Recommended software

### 10.4.2. Guidance on the data analysis methods: An example with QIIME 2

#### 10.4.2.1. Importing data

#### 10.4.2.2. Non-biological sequence removal

#### 10.4.2.3. Sequence quality control (denoising)

#### 10.4.2.4. Removing biological contamination

## 10.5. Applications and limitations

# 11. Data management and open access sharing

## 11.1. Metadata standardization

### 11.1.1. Common problems with Apis-related BioProjects

### 11.1.2. Common problems with Apis-related BioSamples

## 11.2. Sharing pipelines and scripts

# 12. The future of Apis omics: Biological integration

# 13. References

# 14. Data availability statement

# 15. Supplemental online material
