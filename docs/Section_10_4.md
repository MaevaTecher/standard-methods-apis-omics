# 10. Microbiome analysis

## 10.4. Microbiome data analysis

Regardless of whether 16S, 18S, or IST amplicons are used, the general principle is that microbial taxonomy can be inferred by comparing the gene fragment sequence to a specific database. Concurrently, relative abundances can be calculated based on the number of amplicon copies. Below we provide guidance on strategies and softwares that can be used to complete this type of analysis.

### 10.4.1. Recommended software

There are currently several pieces of software used to process amplicon data, either by inferring operational taxonomic units (OTUs) or amplicon sequence variants (ASVs). While OTUs represent a cluster of multiple and similar sequences, for ASVs the differences in nucleotides will result in a unique variant and a more detailed picture of the diversity. We recommend here the **Mothur** pipeline (Schloss, 2020) for quality control of your reads, contig formation, chimera removal, alignment to the 16S rRNA gene, and generation of OTUs and ASVs. For taxonomy, **Mothur** uses Bayesian analysis of kmer profiles, returning the most likely match with the database. All these steps are detailed in the standard operating procedure ([SOP](https://mothur.org/wiki/miseq_sop/)) (Schloss, 2020).

Commonly used databases are SILVA and UNITE, for bacteria and fungi respectively. Several other more curated databases are also available for the study of bee species, such as RDP for annotated bacterial and archaeal 16S rRNA sequences and fungal 28S rRNA sequences (Cole et al., 2014), and BEExact for bacterial 16S rRNA sequences often found in bee species (Daisley & Reid, 2021). The choice of database is important, as it can lead to errors in taxonomic placement if sequence representatives from your environment are misidentified or absent (Newton & Roeselers, 2012).

The next steps may include statistical analyses and plotting results, for which you can continue to follow the **Mothur** SOP or the **QIIME 2** pipeline (see [Section 10.4.2](https://maevatecher.github.io/standard-methods-apis-omics/Section_10_4/)). In general, we recommend measuring alpha diversity to generate rarefaction curves describing the number of OTUs or ASVs as a function of sampling effort, and beta diversity to compare samples’ community structure. Distance matrices can be visualized using the Principal Coordinates Analysis (PCoA) or the Non-metric multidimensional scaling (NMDS) plots. You can also test for the microbiota dynamics with a Permutational Multivariate Analysis of Variance (PERMANOVA) using factors of your choice (*e.g.*, caste, apiary, season, treatments). (Engel et al., 2013) has more information on these exploratory techniques. The **Mothur** wiki ([https://mothur.org/wiki/)](https://mothur.org/wiki/)) has extensive information about data processing in their manual. Here, we provide an alternative worked example using **QIIME 2**.

### 10.4.2. Guidance on the data analysis methods: An example with QIIME 2

**QIIME 2** (Bolyen et al., 2019) and its community (**QIIME 2** forum; [https://forum.qiime2.org/)](https://forum.qiime2.org/)) offer standardized pipelines for the analysis of microbial communities. **QIIME 2** core concepts, hardware/software/metadata requirements, installation, (re)activation, and core applications are easily accessible in Qiime2 documentation ([**QIIME 2** docs](https://docs.qiime2.org/2022.11/)), and not explained in this protocol. Keeping track of the official **QIIME 2** docs is recommended since it will reflect the latest **QIIME 2** release. Herein, we will only present the ITS-specific steps as an example. We will follow the **Casava 1.8** protocol for paired-end demultiplexed sequences.

#### 10.4.2.1. Importing data

Data importation in **QIIME 2** is dependent on the data format. FASTQ documents containing single-end or paired-end sequences are the most common raw data. Forward and reverse sequences are usually referred to as R1 and R2, respectively, while barcode sequences are named I1 (index). FASTQ documents can be either multiplexed (one file per sequence “type”, I1, R1, and/or R2) or demultiplexed (one file per sample, with its corresponding R1 and/or R2 sequences). The most common demultiplexed format is **Casava**, obtained through *Illumina*’s **Casava** software. Although **QIIME 2** has implemented commands for the easy importation of the most common data formats, any other type of data format (supported by **QIIME 2**) will have to be imported through “Fastq manifest” ([https://docs.qiime2.org/2021.8/tutorials/importing/?highlight=casava)](https://docs.qiime2.org/2021.8/tutorials/importing/?highlight=casava)) or similar pipelines.

**Step 1.** To import the data, enter the following commands into the terminal:

``` bash
qiime tools import \
  --type 'SampleData[PairedEndSequencesWithQuality]' \
  --input-path casava-18-paired-end-demultiplexed \
  --input-format CasavaOneEightSingleLanePerSampleDirFmt \
  --output-path demux-paired-end.qza
```

#### 10.4.2.2. Non-biological sequence removal

Imported demultiplexed sequences contain “non-biological” sequences (*i.e*., primers), which have to be removed. Hypervariable-length amplicons such as ITS can contain 4 non-biological sequences: F primer at the beginning of F sequences, reverse complementary sequence of the R primer at the end of F sequences, R primer at the beginning of R sequences, and reverse complementary sequence of the F primer at the end of R sequences.

**Step 2.** To remove these non-biological sequences, execute the following commands:

``` bash
qiime cutadapt trim-paired \
--i-demultiplexed-sequences demux-paired-end.qza \
--p-adapter-f GCATATCAATAAGCGGAGGA \ #Reverse complementary sequence of Rp.
--p-front-f  GTGARTCATCGAATCTTTG \   #Forward primer (Fp) sequence: fITS7 
--p-adapter-r CAAAGATTCGATGAYTCAC \  #Reverse complementary sequence of Fp.
--p-front-r TCCTCCGCTTATTGATATGC \   #Reverse primer (Rp) sequence: ITS4
--p-error-rate 0.1 \   #Allowed error-rate (default)
--o-trimmed-sequences trimmed.qza \
--verbose
```

#### 10.4.2.3. Sequence quality control (denoising)

Denoising in **QIIME 2** can be performed through **DADA2** (Callahan et al., 2016) or **Deblur** (Amir et al., 2017). **DADA2** produces amplicon sequence variants (ASVs) while **Deblur** gives sub-operational-taxonomic-units (sub-OTUs or sOTUs). Herein, we will follow the **DADA2** protocol, wherein paired-end reads are joined and denoised simultaneously. Two parameters are needed: trimming positions (starts of F and R reads) and truncating positions (ends of F and R reads). Both parameters can be determined by visualizing the demultiplexed data and checking the interactive quality plots, which contain quality score values per sequence base.

**Step 3.** Determine trimming and truncating positions:

``` bash
qiime demux summarize \
  --i-data trimmed.qza \
  --o-visualization trimmed.qzv
```

Optimal parameters result in merged reads of good quality. F and R have to be long enough to merge, and merged sequences have to be good enough to pass the filtering threshold of **DADA2**.

**Step 4.** Trim primer sequences:

``` bash
qiime dada2 denoise-paired \ #Perform Dada2 denoising
  --i-demultiplexed-seqs demux-paired-end_trimmed_def.qza \
  --p-trim-left-f 13 \  #Trim Forward sequences in 13rd position
  --p-trim-left-r 0 \   #Do not trim Reverse sequences
  --p-trunc-len-f 0 \   #Do not truncate the end of Forward sequences
  --p-trunc-len-r 220 \ #Truncate Reverse sequences in 220th position
  --o-table dada2/table.qza \
  --o-representative-sequences rep-seqs.qza \
  --o-denoising-stats denoising-stats.qza
```

**Step 5.** Visualize denoising results:

``` bash
qiime metadata tabulate \   
--m-input-file denoising-stats.qza \
--o-visualization denoising-stats.qzv
```

From this point on, paired-end and single-end data are analyzed following the same steps, for all microbial communities. In order to assign taxonomy ID to fungal sequences, the UNITE database is used, which requires to be first trained. It is recommended to train the UNITE classifier as follows:

-   Use non-extracted full ITS sequences from the developer UNITE database (**QIIME-**compatible release).

-   Use the q2-itsxpress plugin, which permits extraction of ITS domains from input data (sequences). Then, extracted sequences can be compared to the standard UNITE database.

Available tutorials for diversity and compositional analysis can be followed at the **QIIME** docs website (<https://docs.qiime2.org/2022.11/>) and a detailed pipeline can be found at (Estaki et al., 2020).

#### 10.4.2.4. Removing biological contamination

Despite best efforts, biological contamination of samples with microbes not belonging to the sample is still possible. Excluding suspected contaminants from downstream analyses is encouraged. For example, excluding suspected contaminants from downstream analyses is appropriate if, according to the sequencing of blank controls, contamination by laboratory reagents or the laboratory environment is suspected. If necessary, there are multiple softwares for removal of contaminant sequences, such as the **R** package **decontam** (Davis et al., 2018; Salter et al., 2014).

