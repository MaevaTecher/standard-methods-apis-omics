# 5. Epigenomics

## 5.2. DNA methylation

### 5.2.1. Bisulfite-seq

Bisulfite sequencing (BS-seq) is a method used to study DNA methylation at the single-nucleotide resolution. The method involves treating DNA with sodium bisulfite, which converts unmethylated cytosine residues to uracil, while leaving methylated cytosine (5mC) residues unchanged. Consequently, after bisulfite treatment, only the methylated cytosines are retained. The treated DNA is then sequenced, and the resulting data can be analyzed to determine the methylation status of each cytosine in the genome. Bisulfite sequencing is widely employed in epigenetics research to elucidate the role of DNA methylation in gene regulation and various diseases.

There are several strategies to study DNA methylation marks, including 1) whole genome bisulfite sequencing (WGBS), 2) reduced representation bisulfite sequencing (RRBS) using restriction digestion of the genomic sequences, or 3) targeted DNA methylation analysis using PCR. In honey bee research, WGBS is most often used, and is covered below.

#### 5.2.1.1. Considerations

-   **Input**: WGBS requires high-quality and high-quantity DNA samples. It is important to have enough DNA to generate sufficient sequencing depth to detect methylation at low-frequency sites. Caution must be taken because the sample processing can degrade DNA to some degree. Sufficient depth can be achieved by using large numbers of sequencing reads, or by using high-throughput sequencing platforms.

-   **Sequencing**: Bisulfite-treated DNA needs to be converted into a sequencing library before it can be sequenced. This typically involves fragmenting the DNA, end-repairing the fragments, and then ligating adapters for sequencing.

-   **Integration**: WGBS data is often compared with other epigenetic data such as ChIP-seq and RNA-seq to understand the functional relevance of DNA methylation.

-   Validation: It is important to validate the WGBS data using other techniques such as pyrosequencing, bisulfite pyrosequencing, or methylation-specific PCR (MSP).

#### 5.2.1.2. Materials

-   **Large equipment**: Thermal cycler for PCRs, downstream sequencing platform such as *Illumina* MethylationEPIC Array, Single Cell Methyl-Seq, Agilent SureSelect MethylSeq (*Agilent Technologies Inc.*), or IDT xGen™ Methylation-Sequencing technologies

-   Kits for bisulfite conversion and genomic library prep such as the EZ DNA Methylation Kits, generally including the M-Binding Buffer, M-Wash Buffer, L-Desulphonation Buffer, M-Elution Buffer, and Bisulfite conversion reagent, spin columns, and collection tubes.

#### 5.2.1.3. Methods

***Wet lab processing:***

1.  Extract total genomic DNA (1 μg per group) from bulk tissue of interest using a total DNA extraction kit (for example, DNeasy Blood & Tissue Kit (*QIAGEN*), Maxwell® RSC Tissue DNA Kit (*Promega*), Quick-DNA Tissue/Insect Kit (*Zymo Research*)).

2.  Use the EZ DNA methylation kit (*Zymo Research*), or equivalent, to perform the bisulfite treatment on all the genomic DNA samples following the manufacturer’s instructions.

3.  Bisulfite conversion reagent (130 µl) is added to a DNA sample (20 µl, DNA quantity range is between 100 pg to 2 µg) in a PCR tube.

4.  Place the mix on the thermal cycler and run the following protocol: 98 °C (8 min), 54 °C (60 min), then 4 °C for overnight (no more than 20 h).

5.  Add the converted DNA to a spin column which has M-Binding Buffer pre-added (600 µl).

6.  Mix the sample and the buffer well, centrifuge for 30 s at > 10,000 *g.*

7.  Add M-Wash Buffer (100 µl) and repeat centrifugation

8.  Add L-Desulphonation Buffer (200 µl) to the column and incubate 15-20 min (room temperature) and repeat centrifugation.

9.  Add M-Wash Buffer (200 µl) to the column and repeat centrifugation. Repeat the wash again.

10. Transfer the column to a microcentrifuge tube (1.5 ml) and add 10 µl M-Elution Buffer, water, or TE buffer (pH value is more than or equal to 6.0) to the column center. Centrifuge 30 s at full speed to collect the DNA.

***Sequencing and quality check:***

11. Sequence the DNA on your preferred sequencing platform following the manufacturer’s guidelines.

12. Check the sequencing data for quality control (QC), processed to align read to the most updated *Apis mellifera* genome (see [Section 5.2.4]). Several key QC measures to consider include the sequence quality, mapping efficiency as general sequencing process, coverage, and the bisulfite conversion efficiency. The coverage of each base should be at least 20x, and ideally higher.

```         
**TIP:** If there is a high duplicate rate, it can indicate issues with library preparation or sequencing. It is generally recommended to have a duplication rate of less than 10%. It is also important to check the efficiency of bisulfite conversion, which can be done by comparing the proportion of C to T transitions in the WGBS data with the proportion of C to T transitions in the input DNA.
```

### 5.2.2. Methylated DNA immunoprecipitation-sequencing (MeDIP-seq)

Methylated DNA immunoprecipitation sequencing (MeDIP-seq) is a tool to identify regions of the genome that are methylated. It is based on the principle that methylated DNA can be selectively pulled down from a sample using an antibody that recognizes 5-methylcytosine 5mC. Basically, the DNA is fragmented and denatured, then incubated with an antibody that specifically binds to 5mC. The methylated DNA is then immunoprecipitated using magnetic beads or protein A/G. The immunoprecipitated DNA is then sequenced, and the resulting data is analyzed to identify regions of the genome that are methylated.

#### 5.2.2.1. Considerations

MeDIP-seq is a powerful technique that can be used to identify methylated regions in a genome-wide manner, and it also allows the detection of low levels of methylation. However, it has some limitations, such as the need for a high-quality antibody that recognizes 5mC and the potential for cross-reactivity with other modified forms of cytosine.

MeDIP-seq data can also be compared with other epigenetic data such as ChIP-seq and RNA-seq to understand the functional relevance of DNA methylation. The MeDIP-seq procedure described here is referenced from (Qinghe Li et al., 2011) and (Shi et al., 2013).

#### 5.2.2.2. Materials

-   DNA template

-   Genomic DNA extraction kit

-   A Quick Ligation kit (*QIAGEN*)

-   MinEluteH PCR Purification kit (*QIAGEN*)

-   IP buffer (Tris-HCl 10 mM with pH 7.5, NaCl 280 mM, EDTA 1 mM)

-   T4 polynucleotide kinase

-   T4 DNA polymerase

-   Anti5-methylcytosine mouse monoclonal antibody (*Calbiochem*)

-   Dynabeads Protein G and Protein A

#### 5.2.2.3. Methods

1.  DNA is isolated by phenol-chloroform extraction, and fragmented (around 200–350 bp), and extracted by a gel extraction kit. The recovered DNA is first 5’ and 3’ end blunting, phosphorylating and repairing by T4 Polynucleotide Kinase and T4 DNA Polymerase.

2.  After adding the ATP in the 3’ end, an *Illumina* sequencing primer adapter is ligated to the DNA using the Quick Ligation kit.

3.  DNA is recovered by MinEluteH PCR Purification Kit (*QIAGEN*) and used for immunoprecipitation (IP).

4.  IP DNA (4 mg) is then heat denatured (5 min), then is incubated with 32 mg anti5-methylcytosine mouse monoclonal antibody in a 400 ml of IP buffer for 30 min at 4 °C.

5.  The Dynabeads Protein G (100 ml) and Protein A (*Dynal*) are added to the mix for incubation of 5.5 hours at 4 °C.

6.  After immunoprecipitation, the DNA is amplified by PCR with specific *Illumina* sequencing primers. *Illumina* platforms such as HiSeq (discontinued), NextSeq, or NovaSeq can be used for sequencing, depending on the cost and coverage needs.

### 5.2.3. Data processing and analysis

The analysis of BS-seq data involves several steps, including data preprocessing, alignment, methylation calling, and downstream analysis. These steps can vary depending on the specific research question and the software tools used.

#### 5.2.3.1. Software recommendations

The first step is to align the preprocessed reads to the reference genome. The most commonly used aligner for BS-seq data is **Bismark**, which is able to align bisulfite-converted reads to the reference genome (Krueger & Andrews, 2011).

After alignment, the next step is to call methylation levels at each cytosine position in the genome. There are several different methylation calling tools available, such as **MethPipe** (Song et al., 2013), **DSS** (Feng & Wu, 2019), and **MethylSight** (Biggar et al., 2020). The model-based analysis of chIPseq (MACS) approach can also be used to measure the methylation levels in the *A. mellifera* genome (Neary & Carless, 2020; Shi et al., 2013).

Once the methylation levels have been called, the next step is to perform downstream analysis to identify differentially methylated regions (DMRs), annotate them with functional elements and explore relationships with other data types such as transcriptomics. There are various tools available for this purpose, such as **MethylKit** (Akalin et al., 2012), **DMRcate** (Peters et al., 2021), and **MethylSeekR** (Burger et al., 2013). These tools use different algorithms to call methylation levels and correct for sequencing errors. The results can be visualized using various tools such as **IGV**, **methylKit** and Bioconductor packages such as **BSgenome** and **BSseq**.

#### 5.2.3.2. Data repository

Like all sequencing data, DNA methylation or RNA methylation data should be deposited in a public database. For example, NCBI Sequence Read Archive (SRA) data portal is a public database for scientists to deposit their raw sequencing data (see [Section 11]).

#### 5.2.3.3. Statistical analysis

Statistical analysis of BS-seq data typically involves the estimation of methylation levels at individual cytosine positions or at predefined regions of interest, such as gene bodies in the case of honey bee genome. The estimation of methylation levels is usually based on the proportion of methylated reads, which are reads that have a cytosine-to-thymine (C-to-T) change due to bisulfite conversion (Foret et al., 2012).

Once methylation levels have been estimated, several statistical methods can be used to identify differentially methylated regions (DMRs) between different samples or groups. Commonly used statistical thresholds for differential methylation are a percent methylation difference larger than 10% and q < 0.01 (Akalin et al., 2012). A Bayesian framework can also be used to estimate the probability of different methylation states at each cytosine position and to identify DMRs.

After DMRs have been identified, several downstream analyses such as functional annotation of DMRs, correlation of DMRs with other epigenetic or transcriptomic data, pathway analysis, or clustering of DMRs to identify patterns of co-regulation can be performed.

