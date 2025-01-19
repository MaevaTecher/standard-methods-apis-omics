# 6. Transcriptomics

## 6.3. Single-cell transcriptomics

RNA-seq has traditionally been done with whole tissue samples also called “bulk sequencing.” However, recent advances in sequencing technology to target smaller input material have made it possible to sequence the transcriptomes of individual cells within a tissue sample while preserving the identity of their cell of origin to create a cell atlas. Single-cell transcriptomics is a relatively new technique developed in 2013 for biomedical purposes and only started to be applied to non-model organisms (Chen, Sun, et al., 2021). This field is uniquely suited to studying gene expression in known heterogeneous tissues and even identifying the spatial structure of cells in tissue downstream.

The approach takes a cell suspension of the tissue of interest, separates cells individually, and assigns a unique barcode to each mRNA transcript in the cell. This allows researchers to achieve incredible resolution within organs even creating cell atlas in mammals, fly and ants (Chen et al., 2021; Li et al., 2022; Li et al., 2022). Recently, Zhang et al., (2022) used the technique to compare the transcriptomes of different types of neurons within the honey bee brain (*e.g.* Kenyon cells, optic lobe cells, olfactory projection neurons, *etc.*), initiating the first cell atlas in bees. Below is a general protocol for single-cell transcriptomics sample preparation adapted from Traniello *et al.* (2020).

### 6.3.1. Considerations

-   Single-cell sequencing requires fresh samples that can readily be dissociated into a cell suspension.

-   If it is not possible to use a fresh sample, the cell suspension (protocol described below) can be made fresh, then frozen and used later for sequencing.

-   Cells embedded in excessive extracellular matrix run the risk of being damaged through dissociation and rendered unusable for sequencing.

-   Different cell types from different tissues (for example brain versus fat body) will need more time to optimize the procedure for cell dissociation by testing different buffers or reagents.

### 6.3.2. Materials

-   Large equipment: 10x chromium controller

-   Pipette and tips

-   Kits: Chromium Chip G Single Cell Kit (*10x Genomics*), Chromium Next GEM Single Cell 3’ Kit (*10x Genomics*) ● RNAse-free 1X PBS

-   1.5 ml microfuge tubes (nuclease-free)

-   Trypsin

-   Ethylene-diamine-tetracetic acid (EDTA)

-   Phosphate-buffered saline (PBS)

-   Dissection plate

-   Dissection forceps and scissors

-   Dissociation media

-   Table centrifuge

-   0.4% trypan blue

● C-Chip disposable hemocytometer and a Compound microscope or a cellometer

### 6.3.3. Sample preparation procedure for single-cell sequencing

1.  Rapidly dissect desired tissue in cold RNase-free 1X PBS and place in a 1.5 ml microfuge tube.

2.  Add PBS with 0.25% trypsin to sample.

3.  Incubate on ice for 30 minutes.

4.  Gently dissociate cells by pipetting with 200 μl pipette tips.

5.  Separate individual brain cells using a *10x Genomics* microfluidics chip following the manufacturer’s instructions.

6.  Prepare single cell transcriptomics library utilizing the Chromium NextGen Single Cell 3’ technology according to manufacturer instructions.

7.  Sequence single-cell libraries utilizing either *Illumina* or *Nanopore* sequencing.

