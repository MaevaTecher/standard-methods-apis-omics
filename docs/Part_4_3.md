# 4. Whole-genome population and association studies

## 4.3. SNP and indel detection

Here we provide a primer on the bioinformatics involved in detecting sequence variants from *Illumina* data, as it is often very difficult to know how to start. The software tools chosen here result from the authors’ positive experience in their application of *A. mellifera* genomics workflow but do not reject the validity and rapidity of alternative algorithms and pipelines. We recommend the review by Bourgeois and Warren (2021) listing the most common software and methods applicable to comparative and population genomics in eukaryotes. For further details on each parameter, future users will have to go to the dedicated websites for **BWA-MEM**, **SAMtools**, **GATK**, **Picard, VCFtools,** and **BCFtools** (Danecek et al., 2011, 2021; McKenna et al., 2010).

### 4.3.1. Mapping reads with **BWA-MEM**: From FASTQ files to BAM files

The first step is to map the short reads to the reference genome to produce a BAM file. Typically, for SNP detection, sequencing is performed paired-end with an *Illumina* instrument, giving millions of \~150 bp reads in which 300-500 bp will separate the beginning of Read 1 (first mate or forward read) and the end of Read 2 (second mate or reverse read), according to the size specification of the sequencing library. For each sample, the sequencing instrument will produce two files in compressed FASTQ format containing the reads. These will have names in the form “AOC5_TAGCTT_L002_R1.fastq.gz” and “AOC5_TAGCTT_L002_R2.fastq.gz”, which includes the sample name (AOC5), the sample identification in the sample sheet (TAGCTT), the lane number on the sequencing machine (L002) and the Read (R1 or R2). One file will contain all Read 1 sequences and another will contain all Read 2 sequences.

In honey bee genomics, there is currently no consensus on a single best mapping software. However, based on our literature survey, we found that **BWA-MEM** (Burrows–Wheeler Aligner), **Bowtie2** and **Stampy** have been used for *A. mellifera* and *A. cerana* short DNA read mapping. However, we noted that **BWA-MEM** was the most commonly used, and it was also reported as one of the top performing short reads aligners (Musich et al., 2021). Therefore, we have chosen BWA-MEM as our current standard software for mapping honey bee genomes.

**Step 1.** Mapping the reads to the reference genome is done here with **BWA-MEM** (Li, 2013) and parsing with **SAMtools** using the following commands:

``` bash
bwa mem -M GCF_003254395.2_Amel_HAv3.1_genomic.fna \
AOC5_TAGCTT_L002_R1.fastq.gz \
AOC5_TAGCTT_L002_R2.fastq.gz | \
samtools view -bh -o AOC5_TAGCTT_L002_aligned.bam -
```

The -M command marks shorter split reads as secondary. As **BWA-MEM** will output a very large file in SAM format, its output is piped (\|) directly into the samtools view -bh command, that will compress directly in the compact BAM format (-b), while including the header (-h).

The full description of the SAM format can be found [online](https://samtools.github.io/hts-specs/SAMv1.pdf), and is updated on a regular basis. Briefly, a SAM/BAM file will contain a header with diverse information, such as if the file was sorted, the name of the reference sequence used, and the programs that were used to process the data (alignment and other subsequent analyses).

**Special considerations**: If a sample was sequenced in two separate runs, lanes or from two different libraries, the best practice is to require the mapping to be done separately and the BAM files produced to be subsequently merged. This is important for backwards traceability and for downstream analyses, as reads from different runs may have specific biases affecting base or mapping quality estimations. In this scenario, sample “BER15” was sequenced in two separate lanes of an *Illumina* instrument. Alignment was done separately, giving two BAM files, to be merged with samtools merge.

**Step 2.** Merge BAM files with mapped reads using **SAMtools**:

``` bash
samtools merge -o BER15_ATCACG_merged_aligned.bam \
BER15_ATCACG_L002_aligned.bam \
BER15_ATCACG_L005_aligned.bam
```

This information is passed on to the BAM file in the mandatory ID tag of the read group (\@RG) lines in the header, and each mate-pair read in the BAM file will be assigned to one or the other ID tag:

``` bash
samtools view -H BER15_ATCACG_merged_aligned.bam | grep ^@RG
@RG     ID:BER15_ATCACG_L002
@RG     ID:BER15_ATCACG_L005
```

**Step 3.** Sort the BAM file using the following commands with **Picard**:

``` bash
java -jar picard.jar SortSam \
    I=AOC5_TAGCTT_L002_aligned.bam \
    O=AOC5_TAGCTT_L002_sorted.bam \
    SORT_ORDER=coordinate
```

### 4.3.2. Marking duplicate reads with **Picard**

During sample preparation and sequencing, DNA amplification steps will be performed, in which case a single DNA fragment can produce duplicate reads. It is important to tag such reads in the BAM file, so that they will be ignored when calling variants with **GATK** HaplotypeCaller.

**Step 4.** Tag the duplicate reads using **Picard** option MarkDuplicates:

``` bash
java -jar picard.jar MarkDuplicates \
    I=AOC5_TAGCTT_L002_sorted.bam \
    O=AOC5_TAGCTT_L002_dedup.bam \
    M=marked_dup_metrics.txt
```

**Step 5.** The reads can then be sorted and indexed with **SAMtools**:

``` bash
samtools sort -T AOC5_TAGCTT_L002_dedup.bam \
-o AOC5_TAGCTT_L002_sort.bam
samtools index AOC5_TAGCTT_L002_sort.bam
```

### 4.3.3. Base quality score recalibration (BQSR) with **GATK**

Sequence reads in the FASTQ format have a quality score associated to each base called by the sequencing machine, which are based on the manufacturer’s algorithms. These express the confidence of the base calling and will greatly influence the algorithms used for variant calling as well as deciding between sequencing errors and real biological differences.

BQSR models non-random technical errors in the data using a machine learning approach and adjusts the scores accordingly. A set of known variants in the VCF file format is provided to mask bases at sites of expected variation. Mismatches outside these sites are counted as errors.

**Step 6.** Use the following **GATK** commands to generate the recalibration table:

``` bash
gatk BaseRecalibrator \
  -I AOC5_TAGCTT_L002_sort.bam \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  --known-sites sites_of_variation.vcf \
  --known-sites another/optional/setOfSitesToMask.vcf \
  -O recal_data.table
```

**Step 7.** Recalibrate base qualities:

``` bash
gatk ApplyBQSR \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  -I AOC5_TAGCTT_L002_sort.bam \
  --bqsr-recal-file recal_data.table \
  -O AOC5_TAGCTT_L002_BQSR.bam
```

### 4.3.4. Calling variants with **GATK**

**Step 8.** Variants can be called for each sample individually using the following **GATK** commands:

``` bash
gatk HaplotypeCaller \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  -I AOC5_TAGCTT_L002_BQSR.bam \
  -O AOC5.g.vcf.gz
  -ERC GVCF \
  -ploidy 2
```

**Special considerations:** The option “-ploidy” is set to 2 (diploid) in the example, which fits for a honey bee worker or queen sample. The option “-ploidy 1” can be used for haploid drones, but in our experience, this leads to false positive SNP detection. A better option is to analyze haploid samples using the diploid model and to filter out SNPs with heterozygote calls in the drones after the genotyping step.

### 4.3.5. Combining all samples and genotypes with **GATK**

At this stage, all individual genotype files will be combined into a single file. If more than hundred samples are processed, this may require a large amount of memory, which can be specified (`--java-options "-Xmx10g"`).

**Step 9.** Combine genotype files:

``` bash
gatk --java-options "-Xmx10g" CombineGVCFs \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  --variant AOC1.g.vcf.gz \
  --variant AOC2.g.vcf.gz \
  --variant AOC3.g.vcf.gz \
  --variant AOC4.g.vcf.gz \
  --variant AOC5.g.vcf.gz \
  --o all_samples.g.vcf.gz
```

**Step 10.** Once combined in a large file, joint genotyping can be performed:

``` bash
gatk --java-options "-Xmx10g" GenotypeGVCFs \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  -V all_samples.g.vcf.gz \
  --use-new-qual-calculator \
  -O all_samples_genotyped.vcf.gz
```

### 4.3.6. Filtering variants with **GATK**: Technical filters

**Step 11.** The following commands will retain only site variants coded as SNPs:

``` bash
gatk SelectVariants \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  -V all_samples_genotyped.vcf.gz \
  --select-type-to-include SNP \
  -O all_samples_genotyped_SNPs.vcf.gz
```

**Step 12.** Variants can then be filtered based on quality scores. First, mark the SNPs in the VCF file that do not pass quality score thresholds:

``` bash
gatk VariantFiltration \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  --filter-expression « QD < 2.0 || FS > 60.0 || MQ < 40.0 »
  --filterName “quality_filters”
  -V all_samples_genotyped_SNPs.vcf.gz \
  -O all_samples_genotyped_SNPs_filter_tagged.vcf.gz
```

Here, we adopted the recommended and generic hard-filtering parameters of all SNP with a variant confidence (QD) below 2, a strand bias (FS) over 60 and a mapping quality (MQ) below 40. However, we recommend readers to always plot these statistics distribution using **R** and **ggplot2** and verify that the thresholds is adapted to their dataset.

**Step 13.** Then, the SNPs that passed the filters can be extracted:

``` bash
gatk SelectVariants \
  -R GCF_003254395.2_Amel_Hav3.1_genomic.fna \
  --exclude-filtered
  -V all_samples_genotyped_SNPs_filter_tagged.vcf.gz
  -O all_samples_genotyped_SNPs_filter_passed.vcf.gz
```

**Special considerations:** If variants were detected in haploid drones using the diploid model, markers having heterozygote calls can now be removed.

### 4.3.7. Filtering variants with **VCFtools**: Data quality

To ensure a high-quality dataset, SNPs should be filtered using not only quality scores, but also, for instance, the mean depth and missing data. Here, the software **VCFtools** (Danecek et al., 2011) is used to include biallelic SNPs (--max-alleles) with at least 5 read depth (--min-meanDP). Further information about SNP filtering, such as the correlation between markers or linkage disequilibrium (LD), can be found in [Section 4.7](https://youneedawiki.com/app/page/1IUnW7oMAEYX0T5pebD3S0LaYgRaxJtc7d96HUFuaPa0?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2).

``` bash
vcftools \
--gzvcf all_samples_genotyped_SNPs_filter_passed.vcf.gz \
--max-alleles 2 \
--min-meanDP 5 \
--out all_samples_filter_2.vcf.gz
```

### 4.3.8. Genotype phasing

Phasing refers to the process of statistical estimation of haplotypes from genotype data. While drone sequencing generates directly phased data, worker or queen sequencing requires an extra step in the analysis for phasing the diploid data. There are several freely available programs for this purpose, such as[**Beagle**](http://faculty.washington.edu/browning/beagle/beagle.html) **5.4** (Browning et al., 2021),[**fastPHASE**](http://stephenslab.uchicago.edu/software.html#fastphase)(Scheet & Stephens, 2006),[**IMPUTE2**](http://mathgen.stats.ox.ac.uk/impute/impute_v2.html) (Howie et al., 2009), and **SHAPEIT4** (Delaneau et al., 2019). **SHAPEIT4** is highly accurate, simple, and computationally fast in large datasets (De Marino et al., 2022). The program can be implemented using the following command line:

``` bash
shapeit4.2 --input all_samples_filter_2.vcf.gz \
--map genomic_map.gmap.gz \
--output phased.vcf.gz
```

### 4.3.9. SNP annotation with **SnpEff**

**SnpEff** is a toolbox to annotate the variants and to calculate their effects (Cingolani et al., 2012). **SnpEff** can be implemented on the [Galaxy](https://usegalaxy.org/;%20see%20section%204.9.2%20step17) analysis platform or by using the following command line:

``` bash
java -Xmx8g -jar snpEff.jar Apis_mellifera all_samples_filter_2.vcf.gz > all_samples_filter_2_annotated.vcf.gz
```

### 4.3.10. SNP analysis by sequencing pooled samples

Pooling offers an alternative for screening populations or subspecies using genome-wide markers and high-throughput technologies. Group-level data obtained from genotyping experiments will deviate from individual-level data in the sense that frequencies of the different alleles observed in the pool, rather than genotype polymorphisms, will be obtained (see [Section 4.2](https://youneedawiki.com/app/page/1Dlftfc-2_gR1pzulaHDakHHMkBNhdY7kYuZb1ldQPm8?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2)[.2]{.underline}). Allele frequencies can be used directly or transformed into mean genotype using **PLINK** (see [Section 4.5](https://youneedawiki.com/app/page/1DcRFPl1JXFf2qRnoRiaAY6bC38v07x6azvPIY-eyYls?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2)[.4.3]{.underline}), or dedicated genotype reconstruction methods. Such methods are currently available to use such allele frequencies, from drone offspring or from a worker pool (Eynard et al., 2022) to obtain queen genotypes. The procedure described here allows the estimation of allele frequencies in pooled samples by using the **PoPoolation** software (Kofler et al., 2011).

#### 4.3.10.1. From FASTQ files to BAM files

Mapping reads and duplicate reads detection are performed as described above ([Section 4.3](https://youneedawiki.com/app/page/1C16yc7avpA8r_aClSNnOCCARWhZgQ_AL0VGIZHd320U?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2)[.1]{.underline} and [Section 4.3.2]{.underline}).

#### 4.3.10.2. SNP selection and pileup files

Each line in a PILEUP file describes a single position in the genome. It contains information on the number of reads “piled up” at the position, together with the base called for each read, if the reads mapped to the forward or the reverse strand and quality scores for the base called for each read. PILEUP files are very large and the detection of SNPs in pooled sequencing is not very effective, so it is best to work on a list of high-quality SNPs that were detected in a previous experiment.

``` bash
samtools mpileup -I -l snp.list \
    -f reference_genome.fa \
    -C 50 -q 20 -Q 20 sample.bam \
    -o sample.pileup
```

The option -I is for skipping indels. The list snp.list is in the form of chromosome position (tab separated). This will generate one PILEUP file per sample. A list of BAM files can be provided (option -l), to make a mpileup file containing multiple samples.

``` bash
samtools mpileup -I -l snp.list \
    -f reference_genome.fa \
    -C 50 -q 20 -Q 20 -b bams.list \
    -o multiple_samples.mpileup
```

#### 4.3.10.3. Counting reads per allele with PoPoolation

**PoPoolation** (Kofler et al., 2011) takes PILEUP files as entries and generates read counts for each possible nucleotide base (A, C, G, or T) at each SNP position reported in the PILEUP file.

``` bash
java -ea -Xmx10g -jar mpileup2sync.jar \
                        --input sample.pileup \
                        --output sample.sync \
                        --fastq-type sanger
```

The sample.sync files present the results in the form of one line per SNP position, with a count of reads for each of A:T:C:G:N:del. The **PoPoolation** suite provides some perl scripts to calculate allele frequency differences or F~ST~ (fixation index) values between pairs of pooled DNA sequences.
