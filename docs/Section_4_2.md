# 4. Whole-genome population and association studies

## 4.2. Ploidy and sampling considerations

Since male bees are haploid and female bees are diploid, the genetic information derived from these samples will be different, and the best sample type will vary depending on the study’s goals. Additionally, sampling individuals versus groups of individuals will change the types of questions that can be answered with the resulting genomic data. Below, we outline some information to help determine what type of sample to work with.

### 4.2.1. Individual sampling

Genotypic information for workers and queens match standard polymorphism data showing three genotypes: homozygous for the reference allele, heterozygous, and homozygous for the alternative allele. Drones, being haploid, only two genotypes: the reference or the alternative allele. Workers provide twice as much data as drones due to their diploid nature, offering better insights into population structure and admixture. However, drone analysis requires less sequencing coverage and is more cost-effective.

### 4.2.2. Pooled sampling

In addition to individual samples, depending on the goal of the experiment, pooled sampling may be necessary. Since workers carry both queen’s and inseminating males’ genetics, a pooled worker sample may capture the entire allelic diversity within a colony at a more affordable cost than individual analysis. In this case, 50% of the pooled workers’ genetics are derived from the queen, whereas the remaining 50% is representative of the patrilines (the cohort of drones that inseminated the queen) of the colony (see [Section 4.3.7](https://maevatecher.github.io/standard-methods-apis-omics/Part_4_3/) for a brief discussion on handling pooled data). Pools can be made from honey bee tissue (*e.g.*, thoraces, flight muscles, heads with compound eyes removed, legs, antennae) or from multiple specimen DNA.

#### 4.2.2.1. Groups of workers

To represent the complete genetic makeup of the meta organism that is a honey bee colony, a large number of individuals should be sampled. This requirement is a consequence of the polyandrous mating system in *Apis* bees with variable degrees across species (Kraus et al., 2005; Palmer & Oldroyd, 2000). While extreme polyandry levels were reported in the giant honey bee *A. dorsata* (up to 102 detected patrilines (Wattanachaiyingcharoen et al., 2003)) the following advices relates *A. mellifera* mating frequency (averaging around 13.8 ± 2.5 males (Palmer & Oldroyd, 2000)). The number of pooled individuals has ranged from n = 12 to 500 (Guichard et al., 2021; Momeni et al., 2021; Rizwan et al., 2020; Saelao et al., 2020), and we recommend sampling and sequencing in the order of hundreds of individuals. For example, if 15 males inseminated the queen and a targeted sequencing depth is 30-fold per patriline is desired, pooling approximately 500 related workers would be necessary. Each worker in the pool would then represent 1/15th of the male genetic contribution of the colony, assuming equal representation of all patrilines.

#### 4.2.2.2. Groups of drones

Alternatively, a group of drones can also be sampled. Pooling drones into the same genotyping experiment will allow indirect inference of the queen’s genetic information, as drones carry the queen’s genetics exclusively. However, to obtain a complete representation of the queen’s genetics, it is still necessary to pool a significant number of drone offspring together (Jones et al., 2020).

