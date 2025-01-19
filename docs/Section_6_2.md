# 6. Transcriptomics

## 6.2. Sequencing technologies

Many of the same sequencing platforms used to sequence genomes can be used for transcriptomes as well (see [Section 3](https://maevatecher.github.io/standard-methods-apis-omics/Part_3_1/): Genomic DNA sequencing, and (Evans et al., 2013)). The major differences between RNA-seq and DNA sequencing are 1) laboratory pre-processing conditions that require ultra-clean and low-temperature handling to limit RNA degradation and 2) the need to convert extracted sensitive RNA into double-stranded cDNA. Once transformed into cDNA, the material is stable and can be processed similarly to gDNA. Here, we describe specific considerations when applying this technology to transcriptome sequencing.

### 6.2.1. Considerations

-   Always use proper microbiological aseptic techniques when working with the RNA and RNA-seq library to avoid degradation and cross-contamination. Transcript sequencing output will depend on the initial quality (RIN) and RNA degradation levels (Gallego Romero et al., 2014).

-   Wear and change frequently disposable gloves to prevent RNase contamination and work as quickly as possible until cDNA is prepared.

-   Keep tubes closed and on ice or cold block whenever possible.

-   Be aware that as sequencing technology progresses, the platform chemistry can shift quickly. This can cause discordance in the data output and yield of the same RNA library sequenced (De-Kayne et al., 2021).

-   Downstream analysis such as differential gene expression analysis are sensitive to the number of replicates chosen per condition. A too low sample size may ignore natural variation and can be prone to false discoveries (Y. Li et al., 2022; Squair et al., 2021).

### 6.2.2. *Illumina* sequencing (short reads)

Similar to genome sequencing, *Illumina* is the technology most often used for transcriptomic studies. Short reads are ideal for samples with low RNA yield, and it is relatively quick and inexpensive compared to other sequencing technologies. However, because this technology sequences many short strands with a fragment size ranging from 150-250 bp (Quail et al., 2009), reads from genes with multiple splice variants cannot always be mapped to a specific spliceoform. There are numerous resources describing short-read RNA sequencing and data analysis best practices (Conesa et al., 2016)*,* which, combined with sample handling and RNA extraction protocols previously described specifically for honey bees (Evans et al., 2013), are directly applicable to honey bees. Here, we will focus on long-read sequencing and single-cell transcriptomics, but include updates to short-read sequencing covered in the previous BEEBOOK (Evans et al., 2013).

### 6.2.3. Third generation sequencing (long reads)

Third-generation sequencing enables the user to sequence contiguous and long reads from molecules of \>10 kb on average, which minimizes some of the computational workload needed to analyze full length transcripts, improves the accuracy of the alignments against the reference genome, and helps resolve ambiguous splice variants.

The main platforms for generating long reads include Oxford Nanopore Technology (ONT) and Isoform sequencing (ISO-seq) using Single-molecule, Real-time (SMRT) sequencing by *PacBio*. RNA extraction and sample handling for analysis by these platforms are essentially as previously described in Evans *et al.* (2013), with scrupulous attention to maintaining RNA integrity. Once RNA is extracted, the kit each sequencing platform manufactures, which are appropriate for their devices, should be used (for example, the Direct RNA or cDNA Sequencing Kit from ONT, or SMRTBell™ kit from *PacBio*).

#### 6.2.3.1. Considerations for choosing a long-read platform

-   ONT has developed sequencing platforms to sequence RNA directly, without conversion to a cDNA intermediate. This minimizes the possibility of errors that could arise during a reverse transcription reaction, but the samples themselves are less stable leading up to sequencing.

-   SMRT *PacBio* sequencing technology is an especially powerful platform because of its ability to generate long reads by reading a single molecule multiple times, which improves sensitivity.

