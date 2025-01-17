# 4. Whole-genome population and association studies

## 4.7. Population genomics: Filtering and summary statistics using **PLINK**

In this section, we will describe some tools available for analyzing SNPs (the most common type of genetic variation used in genomic studies) using a population genomics framework. We will employ a VCF tutorial file containing 3,669,288 SNPs obtained after the variant calling of 33 individuals, 26 of which are of M-lineage ancestry (18 *A. m. iberiensis* and eight *A. m. mellifera*) and seven are of C-lineage ancestry (three *A. m. carnica* and four *A. m. ligustica*).

The first step in any population genomics study is understanding and filtering the dataset by calculating summary statistics to evaluate missing data, allele frequencies, or linkage disequilibrium. To that end, several tools tailored for handling whole-genome data are publicly available, including **VCFtools** (Danecek et al., 2011), **PLINK** (Purcell et al., 2007), and several **R** packages such as **pegas** (Paradis, 2010) and **PopGenome** (Pfeifer et al., 2014). Here, we chose the highly versatile and efficient **PLINK** tool to illustrate the steps involved in filtering and in producing summary statistics for whole-genome datasets.

**PLINK** is a command-line software that runs on different operating systems such as Linux, Microsoft DOS, and macOS. Additionally, instead of using command lines, one can also use an interface through the program **gPLINK**, although this is only available for the most commonly-used commands. In this section, we will go over some of the basic commands that can be carried out with **PLINK** (version 1.9).

### 4.7.1. Download and installation

First, download **PLINK 1.9** (www.cog-genomics.org/plink2/) and the tutorial dataset called *pop_gen*, which can be found on [github.com/MaevaTecher/standard-methods-apis-omics](https://github.com/MaevaTecher/standard-apis-omics). All the commands will be typed at the command prompt. To check that **PLINK** is installed, type “./plink” on the command prompt, and some information about the **PLINK**, like its version and examples of flags, will be printed.

### 4.7.2. Input format and conversion

**PLINK** can operate with various input formats, the most common are regular PLINK TXT files, PLINK 1 binary BIM file, and variant call format (either VCF or BCF). *PLINK 1 binary* is the preferred input format because **PLINK** automatically converts the other formats to this one to save time and space. There are commands for converting the formats to each other. We will explain the most common files and provide the command line to convert them to others.

#### 4.7.2.1. Variant call format (VCF)

Genome sequence data is very often represented in the variant call format (VCF) or its binary counterpart (bcf). The following command can be used to convert vcf into the *PLINK 1 binary* format:

``` bash
plink --vcf pop_gen.vcf \
--keep-allele-order \
--allow-extra-chr \
--make-bed \
--out pop_gen
```

The meanings of the flags are the following:

`--vcf` specifies that we are using a .vcf.gz file.

`--keep-allele-order` specifies that the reference allele will be in the 6th column (A2) and the alternate allele in the 5th column (A1). If we do not use this flag **PLINK** will reorder the alleles, and in A1 and A2 columns will be the minor and major alleles, respectively.

`--allow-extra-chr` indicates that chromosome code does not start with a digit.

`--make-bed` specifies that *PLINK1 binary files* should be generated.

`--out` specifies the output name. If one does not use `--out`, **PLINK** will call the file ‘plink’, for instance ‘plink.bed’.

If there are no errors, four files will be created: *pop_gen.bed*, *pop_gen.bim*, *pop_gen.fam* and *pop_gen*.*log*. The *pop_gen*.*log* file contains the command and other information that was printed to the console. The other files are explained below.

#### 4.7.2.2. PLINK 1 binary format (.bim)

To work with PLINK 1 binary format, the three following files (*pop_gen.fam, pop_gen.bim, and pop_gen.bed*) will be needed:

1\.  *pop_gen.fam*: Contains the sample information and has the following fields:

-   Family ID (If unknown, use the individual ID)

-   Individual ID (Alphanumeric ID to uniquely identify an individual and cannot be ‘0’)

-   Paternal ID (If unknown, use ‘0’)

-   Maternal ID (If unknown, use ‘0’)

-   Sex code (Use '1' if male, '2' if female, '0' if unknown)

-   Phenotype value (Use '1' if control, '2' if case, if not used set to ‘0’)

2\.  *pop_gen.bim*: Contains the variant information and has the following columns:

-   Chromosome (It should be a digit, otherwise one needs to use the flag --keep-allele-order)

-   Variant identifier (Can contain any character, except spaces, tabs or ‘\*’)

-   Genetic distance in morgans or centimorgans (Can be set at ‘0’)

-   Base-pair coordinate (Positive integers in bp)

-   Allele 1-A1 (Contains the less common allele or the alternate allele)

-   Allele 2-A2 (Contains the most common allele or the reference allele)

3)  *pop_gen.bed*: Binary biallelic genotype data.

To convert *PLINK 1 binary* format to VCF, one can use the following command:

``` bash
plink --bfile pop_gene \
--recode vcf \
--out pop_gene
```

`--bfile` specifies that we are using *PLINK 1 binary* format.

`--recode vcf` specifies to create a VCF file as an output.

`--out` specifies the output name.

**Note:** To do this conversion, one needs to be sure that in *PLINK 1 binary* format, the reference alleles are located in the 6^th^ column (A2).

#### 4.7.2.3. Regular PLINK text files

The regular **PLINK** text files are formed by the PED and MAP files. The PED file is a white-space delimited file that stores the genotype calls. It contains six mandatory fields/columns which correspond to the *file.fam*fields. After these columns, the PED file is followed by 2\*(number of variants) columns with the genotype of each locus in the same order as in the MAP file. The MAP file contains the variant information corresponding to the first four columns of *pop_gene.bim*.

The MAP file should have the same root name as the PED file and contain the same number of loci. For instance, if there are genotypes for 10 loci and 12 individuals, the MAP file will contain 10 lines and four columns, and the PED file will contain 12 lines and 26 columns (10 loci \*2 + 6 mandatory columns). The loci in the PED file do not have to comply with the genomic order, but they must be in the same order as in the MAP file.

To convert *PLINK 1 binary* format to *regular PLINK text* file, one can use the following command:

``` bash
plink --bfile pop_gene \
--recode \
--out pop_gene
```

To convert a *regular PLINK text* file to 1 binary PLINK file, the following command can be run:

``` bash
--make-bed \
--out pop_gene
```

If there are no errors, four files will be created: *pop_gene.bed*, *pop_gene.bim*, *pop_gene.fam*, and *pop_gene.log*.

#### 4.7.2.4. Filtering and handling missing data

It is common for genome-wide datasets to have individuals or variants with missing data. This is particularly frequent and expected in low-coverage sequencing data. **PLINK** allows us to estimate the missing data per individual and loci using the flag --missing. A report containing the missing data per Individual ID (*pop_gen.imiss*) and variant (*pop_gen.lmiss*) can be created using the following command:

``` bash
plink --bfile pop_gen --missing --out pop_gen
```

It is highly recommended to discard individuals or variants with high levels of missing data. The missing data thresholds are arbitrary, but values of 10% to 30% are commonly used in the literature (Henriques, Wallberg, et al., 2018; Melanie Parejo et al., 2016; Wallberg et al., 2014; Wragg et al., 2016). To remove the variants with \> 20% missing data (--geno 0.2) and individuals with \>10% missing data (--mind 0.10), for example, the following command can be run:

``` bash
plink --bfile pop_gen \
--geno 0.2 \
--mind 0.1 \
--make-bed \
--out pop_gen_MD 
```

After implementing this command, a *PLINK 1 binary* fileset, with the root name of “pop_gen_MD”, without the problematic individuals and loci, will be created. Note that **PLINK** first removes individuals with too much missing data, and secondly the variants.

#### 4.7.2.5. Computing and filtering based on allele frequency

**PLINK** calculates allele frequencies and filters variants with a minor allele frequency (MAF) lower than an arbitrary threshold, which is commonly set at 1% or 5%. To generate a report (*pop_gene_MD.frq*) containing allele frequencies for each variant, the following command can be run:

``` bash
plink --bfile pop_gen_MD \
--freq \
--out pop_gen_MD 
```

`--freq` specifies calculating the allele frequency for each variant from this dataset.

In the report generated using this command, the first and second columns contain the chromosome and the variant ID followed by the code of the minor (3^rd^ column) and major (4^th^ column) variants and the frequency of the minor allele (5^th^ column). The last column (6^th^) contains the number of allele observations.

To remove the variants with MAF \< 5%, for instance, and create a new file set (here called *pop_gen_MD_maf005*), the following command can be run:

``` bash
plink --bfile pop_gen_MD \
--maf 0.05 \
--make-bed \
--out pop_gen_MD_maf005 
```

`--maf` specifies that only alleles with a minimum minor allele frequency of 5% will be kept in the dataset.

#### 4.7.2.6. Computing differentiation indices: Wright's F~ST~

PLINK also allows calculating the fixation index F~ST~ values for each variant using the Weir and Cockerham method (Weir & Cockerham, 1984). To do so, the flag --fst must be combined with the flag --withinfollowed by the name of the file that specifies the sets of subpopulations to be used. In the tutorial example, the within the file, called *within_M_C_ind*, contains the Family ID in the first column, the Individual ID in the second column, and in the third column the digit 1 to identify one subpopulation (here the C-lineages subspecies) and 2 to identify the second subpopulation (here the M-lineage subspecies).

To calculate the variants’ F~ST~ values between M and C-lineage, the following command can be run:

``` bash
plink --bfile pop_gen_MD_maf005 \
--fst --within within_M_C_ind \
--out pop_gen_MD_maf005
```

A report called *pop_gen_MD_maf005.fst* will be generated. This report contains six columns. The first three columns contain the chromosome number, the variant ID, and the base-pair coordinates, followed by the number of called variants or non-missing genotypes (NMISS), and the 5^th^ column contains the F~ST~ values.

#### 4.7.2.7. Estimating linkage disequilibrium

Linkage disequilibrium (LD) is the non-random association of alleles at different loci. When working with whole-genome data there will be thousands of loci that are in linkage disequilibrium due to different evolutionary forces, but also, because they are physically linked. Some analyses require the use of loci that are in linkage equilibrium (not associated), and **PLINK** provides an easy way to do so, for example, by using the following command:

``` bash
plink --bfile pop_gen_MD_maf005 \
    --indep-pairwise 50 
```

The flag `--indep-pairwise` requires three parameters: the window size, the number of SNPs to shift each step and r^2^. The values of r^2^ range between 0 and 1. When r^2^ = 1, the loci provide exactly the same information. When r^2^ = 0, the loci are in perfect equilibrium. Here, LD is calculated between each pair of SNPs using a window of 50 SNPs. If one pair of SNPs has r^2^ \> 0.5 one of them will be removed. After that, the window will be shifted to five SNPs, and the procedure is repeated until all SNP pairs are examined. Note that lower values of r^2^ and bigger window sizes will remove more loci.

After running this command, two files will be created, one is named *plink.prune.in*, which contains the loci that will be retained (r^2^ \< 0.5), and the other one is named *plink.prune.out*, which contains the loci that will be discarded. These files can be used as arguments of the flags `--extract` (*plink.prune.in*) or --exclude (*plink.prune.out*).

To extract to a new datafile the loci that are in the file *plink.prune.in, the* following command can be run:

``` bash
plink --bfile pop_gen_MD_maf005 \
--extract plink.prune.in \
--make-bed \
--out pop_gen_MD_maf005_pruneddata 
```

Sometimes we do not want to discard SNPs, but we want to calculate the LD in our data. LD can be computed using the flag `--r2`. However, to reduce the output size, only the pairs with r^2^ \> 0.2 and within a distance \< 1 Mb will be printed in the output by default. To modify these thresholds, the flag `--ld-window` or `--ld-window-kb` is used to specify the maximum distance between loci and the flag `--ld-window-r2` is used to specify the minimum r^2^. Using the following command, the r^2^ values will be obtained for all pairs of loci with r^2^ \> 0.5 in a window of 50 Kb. The output called *pop_gen_MD_maf005_pruneddata*.*ld* will be created, and the r^2^ values will be placed in the 7^th^ column.

``` bash
plink --bfile pop_gen_MD_maf005_pruneddata \
--r2 \
--ld-window-kb 50 \
--ld-window-r2 0.5 \
--out pop_gen_MD_maf005_pruneddata
```

`--r2` specifies to compute the linkage disequilibrium.

`--ld-window-kb` specifies the maximum distance between two loci in kilobases.

`--ld-window-r2` specifies the minimum r^2^ to be printed out.

**PLINK** also allows haplotype blocks to be detected in the genome using the flag `--blocks`. If arguments are not provided to this flag, the default options will be implemented. One of them is related to the maximum block size, which is by default 20 kb. To cancel this default flag, the argument no-small-max-span can be used. The flag `--blocks` without arguments assumes that in the dataset, there are phenotypes in the 6^th^ column of the PED or FAM files. If there is no phenotype data, the argument no-pheno-req is required. By default, the pairwise LD is only calculated for variants within 200 kb. If needed, this parameter can be changed using the flag `--blocks-max-kb`. An example of a command to calculate blocks along the honey bee genome can be:

``` bash
plink --bfile pop_gen_MD_maf005 \
--blocks no-pheno-req no-small-max-span \
--blocks-max-kb 5000 \
--out pop_gen_MD_maf005
```

Two files called *pop_gen_MD_maf005.block* and *plink.blocks.det* will be created. Each line of these files represents a block. The file *pop_gen_MD_maf005.block* contains the variant IDs found in each block whereas *plink.blocks.det* contains their positions. If there are 10 variant IDs or positions in one line, it means that the block contains 10 SNPs.

