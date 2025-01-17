# 3. Genome sequencing

## 3.4. Small and large variant detection

The technology most often used for small and large variant detection (SNPs and indels, respectively) is *Illumina*, due to its high throughput, cost-effectiveness, and low error rate. When short reads are produced for each individual and aligned on the reference sequence, sequence differences between the reads and the reference can be observed, indicating the presence of variants. The bioinformatics analyses concerning SNP detection are described further in [Section 4.3](https://youneedawiki.com/app/page/1C16yc7avpA8r_aClSNnOCCARWhZgQ_AL0VGIZHd320U?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2). Small variant detection can also be performed by pool sequencing, in which DNA from multiple samples are mixed prior to indexing and sequencing. Pool sequencing helps in reducing library preparation time and sequencing cost for estimating allele frequencies in populations.

To detect large variants, such as insertions or deletions of several hundred or thousands of base pairs (indels), either two *de novo* assembled genomes will have to be compared, as described further in [Section 4.4](https://youneedawiki.com/app/page/1gNsPlwy9uBCadjKRcnGuEeNalboStTsKx4gl9vGIu68?p=1rc183pyLOH9HstkT14kQP-SXKx-dffa2) using the software **LAST** (Frith & Kawaguchi, 2015), or long reads produced by *PacBio* or *Nanopore* sequencing are aligned onto the reference for breakpoint detection. A common alternative to using **LAST** is **minimap** (Heng Li, 2018) or **LASTZ** (Harris, 2007).

### 3.4.1. RAD-seq

Restriction site-associated DNA sequencing (RAD-seq) is a technology by which a reduced representation of the genome is selected using restriction enzymes and PCR. Typically, 10% of the genome is selected for analyses to reduce the volume of sequencing reads required for SNP detection. However, given the small size of the honey bee genome, the number of reads obtained in an *Illumina* sequencing run is not the limiting factor. From our experience, using RAD-seq in honey bees now will increase the cost of library preparation and, by extension, the overall cost of sequencing while producing data for only a fraction of the genome. Moreover, bioinformatics analyses are slightly more complex than whole genome sequencing, and polymorphisms within the restriction sites used can cause allelic drop-out.

