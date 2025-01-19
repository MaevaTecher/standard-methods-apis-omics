# 10. Microbiome analysis

## 10.3. Amplicon sequencing

Gene-based markers for bacterial and fungal identification, also known as amplicon sequencing or metabarcoding, is often performed through bacterial- or fungal-specific marker gene sequencing. *16S rRNA* gene amplification is the most common for bacteria, while the *18S rRNA* gene or the internal transcribed spacer (ITS) are used for fungal analysis (Romero et al., 2019). The *16S rRNA* gene is constituted by 9 hypervariable regions (V1-V9) surrounded by conserved sequences (Chakravorty et al., 2007) , which are conserved yet variable enough to be differentiated in most bacterial species. The eukaryotic *18S rRNA* gene is not as conserved as its prokaryotic equivalent and often results in unidentified taxa (Frau et al., 2019). Longer ITSs (ITS1, ITS2, and the *5.8S rRNA* gene), however, have been successfully used to identify fungal gut species in honey bees (Decker et al., 2023; Nguyen & Rehan, 2022; Wen et al., 2017; Yun et al., 2018). The approach described below provides a generic guide for how to conduct amplicon sequencing for microbiome analysis, for which any of the abovementioned targets could be used. Important differences would be the design of the primer (specific to the target) and the amplification conditions.

### 10.3.1. Considerations

-   The choice of primer can alter diversity estimates and may alter the annealing efficiency for certain templates. Due to the sequence-length variation of ITS (Frau et al., 2019), it is important to carefully choose the pair of primers and sequencing platforms to use. We suggest following the [Earth Microbiome protocols](https://earthmicrobiome.org/protocols-and-standards/) to choose primers for the amplification of 16S rRNA, 18S rRNA, and ITS barcode genes. Primers can be ordered directly from *Integrated DNA Technologies* (*IDT*) or *Eurofins*.

-   We recommend buying the primers with adapters and barcodes included to reduce the handling and library synthesis cost downstream. For paired-end read sequencing in *Illumina* platforms, we also recommend targeting regions that will ensure a sequence overlap of at least ~50 bp.

-   Conduct PCR for each primer pair in triplicate for each sample. These triplicate samples will be pooled at the end of amplification and serve to reduce random PCR artifacts across your reactions. Use a consistent quantity of DNA input (*e.g.,* 200 ng).

-   Use a proofreading high-fidelity polymerase (*e.g.*, Phusion® High-Fidelity PCR Master Mix with HF Buffer, *New England Biolabs*, *Inc*) to limit spurious artifactual diversity introduced in your amplification of the genes.

-   Negative control samples should always be sequenced. Some bacterial taxa are known contaminants derived from sample processing (*e.g.* DNA extraction kits) (Salter et al., 2014), while different sequencing platforms might favor amplification of specific microorganisms.

-   Batch effects cause significant differences across experiments, unrelated to biotic factors. These effects are major issues in microbiome data, and common when processing samples using multiple sequencing runs. Thus, it is a good idea to always select a set of samples to use as a reference, which will be added to all sequencing runs of an experiment.

-   Amplicon sequencing depth will strongly depend on the expected diversity of the gut microbiome (more diversity requires a higher depth to sample the community). Considering the published work on the bee microbiome, for example, we would recommend a first sequencing depth of 5,000 reads/sample.

-   Demonstrated examples for [bacterial](https://emea.support.illumina.com/downloads/16s_metagenomic_sequencing_library_preparation.html) and [fungal](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/metagenomic/fungal-metagenomic-demonstrated-protocol-1000000064940-01.pdf)) amplicon sequencing can be found on the Illumina website.

### 10.3.2. Materials for amplicon sequencing

-   Kits: PureLink PCR Purification Kit (Invitrogen), Quant-iT (Invitrogen), Nextera XT DNA Library Preparation Kit (*Illumina*), MiSeq Reagent Kit v2 (*Illumina*)

-   Equipment: PCR thermocycler, fluorescent spectrophotometer (compatible with 96-well plates), MiSeq instrument (*Illumina*) agarose gel electrophoresis apparatus and associated reagents

-   Reagents: Phusion® High-Fidelity PCR Master Mix with HF Buffer (*New England Biolabs*, *Inc*). Forward and Reverse primers to target the particular gene of interest (*e.g.* 16S rRNA, 18S rRNA, ITS)

-   PCR plates

### 10.3.3. Methods for amplicon sequencing

1.  Mix a defined quantity of DNA with 1 X of Phusion® High-Fidelity PCR Master Mix with HF Buffer (*New England Biolabs*, *Inc*), forward and reverse primers to a final concentration of 0.5 µM, in a final reaction volume of 50 µL.

2.  In the thermocycler run an initial denaturation at 98 °C for 2 min, followed by 30 cycles of 98 °C denaturation for 10 s, 55 °C annealing for 30 s and 72 °C extension for 30 s, with a final extension step at 72 °C for 10 min. **TIP:** Be attentive to primer melting point requirements and change the annealing temperature if needed.

3.  Check for the amplicon size in a 1 % agarose gel and then purify the PCR product with PureLink PCR Purification Kit following the manufacturer's recommendations. If you did not include barcodes in your primer synthesis, you must prepare libraries with the Nextera XT DNA Library Preparation Kit, following the manufacturer's instructions, using one barcode per sample.

4.  The amplicons produced as part of this protocol must be normalized by concentration and pooled for sequencing. If you will be pooling your samples yourself, we recommend using the Quant-iT kit, as per manufacturer instructions.

5.  After pooling your sample such that the same amount of DNA from each amplicon is added to your sequencing run, you will clean up your PCR amplicons using the PureLink PCR Purification Kit again.

6.  These amplicons should be sequenced using 2 × 250 paired-end reads on a Miseq platform using the MiSeq Reagent Kit v2.
