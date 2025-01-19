# 10. Microbiome analysis

## 10.2. Sampling and DNA extraction

### 10.2.1. Considerations

#### 10.2.1.1. General

-   If you won’t be able to use the fresh samples for the DNA extraction or would like to culture microbes from them later, you may follow the procedures for sampling or dissection, then macerate each sample in individual tubes with 1X PBS, add glycerol to a final concentration of 25% and store them at -80 °C until use.

-   Change dissection and sample collection instruments (tweezers, scissors, scalpels, spoons, *etc*.) between samples. If you don't have the option of using individual tools per sample, you can clean instruments between dissections by dipping them in 70% ethanol and flame sterilizing them, or use disposable individual scalpel sterile blades.

-   It is a good practice to check for DNA quality and quantity in a 1% agarose gel and Qubit Fluorometer, or directly in an 4200 TapeStation (*Agilent Technologies Inc.*), following quality parameters stated by the manufacturer.

-   Controlling cross-contamination is essential. Spin tubes before opening them, especially after incubation steps, to avoid contamination due to any drops inside the caps.

-   You must include negative controls along with the whole experiment: DNA extraction, PCR (in the case of amplicon sequencing), library preparation, and sequencing. These negative controls should be obtained following the exact same protocol as the regular samples, but substituting sample by the buffer. This will allow you to identify contaminants in your sample post-sequencing.

-   In addition to relative quantities, you can also recover absolute quantities of microbiome members by using a spike-in standard control containing accurately quantified cell numbers of specific microbe combinations.

#### 10.2.1.2. Tissue sample handling

-   If your investigation will focus on the microbes associated with internal organs, you may consider surface-sterilizing the larvae or adult bee to ensure you do not contaminate your sample. However, this is a time-consuming step that may not have a significant impact on results[ ](https://www.zotero.org/google-docs/?4dR7ii)(Hammer et al., 2015).

-   The same protocol makes use of commercial kits and suggests specific sequencing platforms for the purpose of presenting a complete procedure. However, while certain steps are essential for reliable microbiome characterization – as indicated in the protocol – the materials used can be replaced according to availability.

#### 10.2.1.3. Hive material sample handling

-   Considering the multiple sources of pollen and saliva in bee bread, the pooling of multiple cells (≥ 10 cells) is recommended to obtain a representative sample. If possible, the targeted cells to be used for DNA extraction should be located on both sides of the comb and on different comb edges.

-   Bee bread physicochemical characteristics change over time and affect the bee bread microbiome. Thus, sampling bee bread cells of similar ages is also recommended. Recently packed pollen cells will have separated layers and a porous, chalky texture, crumbling easily. Older bee bread will still have various layers, but with a more waxy and shiny texture.

-   For sampling hard surfaces, *e.g.* the hive entrance, we recommend using cotton-headed swabs, which facilitate in-field sampling, sample transportation, and storage. The drawback of this sampling method is the low DNA load, often paired with low absorbance scores (< 10 ng/μl).

### 10.2.2. Protocol for tissue samples

#### 10.2.2.1. Materials

-   Kits: DNeasy Blood & Tissue Kit (*QIAGEN*) and complementary reagents.

-   Equipment: Dissection microscope, bead-beating tissue homogenizer (*e.g.* FastPrep-24™ 5G, (*MP Biomedicals*); or Precellys-24, (*Bertin Technologies)*), microtubes, pipettes, and tips (10 - 1000 ul).

-   Reagents: 70% ethanol, 1X PBS, 0.1% sodium hypochlorite solution and 0.22 μm filtered or autoclaved water (optional).

-   Disposable dissection tools or materials for quick sterilization of tools between samples (70% ethanol and a flame).

-   Sample tubes suitable for a bead-beating homogenizer (*e.g.* Lysing Matrix E tubes, (*MP Biomedicals*))

#### 10.2.2.2. Dissection methods

1.  Clean and sterilise bench and tools with 70% ethanol.

2.  Rinse the bee’s body for 3 min in 0.1% sodium hypochlorite and then 3 times in filtered, autoclaved water (optional; see Considerations).

3.  Dissect each tissue sample with a new, sterile microdissection tool to avoid cross-contamination. See Carreck *et al.* (2013) for guidance on dissecting specific tissues.

4.  Place the tissue sample in a homogenization tube and proceed to lysis ([Section 10.2.2.3]{.underline}.). **TIP:** If you are only interested in the bacterial fraction, a lysozyme treatment for bacterial cell wall lysis before DNA extraction may also be a good lysis option.

#### 10.2.2.3. DNA extraction methods

5.  Add your sample to a Lysing Matrix E tube with 400 µL of 1X PBS. Homogenize in FastPrep-24™ 5G for 45 s at speed 6 m/s.
6.  Transfer 180 µl of the sample to a new tube, add 20 μL of proteinase K from DNeasy Blood & Tissue Kit (*QIAGEN*) and incubate the samples for 2 h at 56 °C. Vortex occasionally during incubation.
7.  Add 4 µl RNase A (100 mg/ml), mix by vortexing, and incubate for 2 min at room temperature (~ 22°C).
8.  Continue by following the recommended steps of the DNeasy Blood & Tissue Kit (*QIAGEN*) manufacturer’s protocol for “Purification of Total DNA from Animal Tissues (Spin-Column Protocol)”. For a small amount of initial tissue (*e.g.*, 1 bee gut) elute the DNA in the final step with 2 x 30 μL of AE buffer to improve yields.
9.  Store the DNA samples at ≤ -20 °C until ready for sequencing.

### 10.2.3. Protocol for sampling hive materials

Bee bread is a sugar-rich mixture of packed pollen, nectar, honey, and enzymes derived from the saliva of honey bees (Anderson et al., 2011). Bee activity and lactic acid bacteria acidify this mixture over time, resulting in decreased bacterial yet increased fungal populations (Disayathanoowat et al., 2020). The bee bread bacteriome is dominated by Proteobacteria and Actinobacteria (Anderson et al., 2011; Disayathanoowat et al., 2020; Muñoz-Colmenero et al., 2020).

The hive entrance, on the other hand, acts as a barrier, separating the hive interior and exterior. Thus, this hive niche can be used to detect and measure organisms entering or leaving beehives. However, there is scarce knowledge regarding the microbial diversity and composition of this beehive niche.

#### 10.2.3.1. Materials

-   Kits: QIAamp DNA Mini Kit (*QIAGEN*)

-   Equipment: thermal mixer, vortex, and centrifuge, pipettes, pipette tips, microtubes, chemical hood (bee bread samples only), sterile cotton swabs (hive entrance samples only)

-   Reagents: 1x PBS, 96-100% ethanol (to prepare kit solutions)

-   For bee bread samples only: phenol:chloroform:isoamyl alcohol (25:24:1, v/v), chloroform (>99%)

#### 10.2.3.2. Methods for bee bread sampling and DNA extraction

1.  In a comb piece containing bee bread, locate a non-broken and preferably full cell.

2.  Depending on sample consistency, introduce either tweezers depth inside the cell (at each side of the bee bread) or a large pipette tip (*i.e.* cut 1000 μl tips) through the center.

3.  Pull out the bee bread carefully, shaking gently, and introduce it into a clean tube large enough to hold pooled samples (2-15 mL). Break the bee bread inside the tube to facilitate subsequent steps

4.  Repeat steps 1-4 until an appropriate number of cells are obtained.

5.  Add 1 mL of 1x PBS per cell (*i.e.* 4 mL to a tube containing samples from 4 cells) and homogenize (pipetting) until the sample is uniformly suspended.

6.  Transfer 200 μl of sample to a new tube. The remaining sample can be stored at -20 °C (-80 °C, ideally) in case the extraction must be repeated.

7.  Add 40 μl of proteinase K and 400 μl of Buffer AL, vortex (~15 seconds) and incubate at 56 °C (mixing at 600 rpm) for 1 hour.

8.  Now, work in a fume hood. Transfer the supernatant to a new tube, add 600 μl of phenol:chloroform:isoamyl alcohol, vortex intensely, and centrifuge for 15 min at 14,000 rpm. **NOTE:** For lab space in which hazardous agents phenol:chloroform can not be used, we recommend the usage of commercial kits dedicated to microbiome DNA extraction as an alternative

9.  Transfer the supernatant to a new tube, add 600 μl of chloroform, vortex intensely, and centrifuge for 5 min at 14,000 rpm.

10. Transfer the supernatant to a new tube, add 400 μl of 96-100% ethanol, vortex briefly (~15 seconds), and spin.

11. Working in the fume hood is no longer necessary. Transfer the sample (supernatant from step 10) to the column (no more than 700 μl) and follow the established DNA extraction protocol for the kit, until eluting the DNA in 60 μl of buffer AE.

12. Store the DNA samples at ≤ -20 °C until ready for sequencing.

#### 10.2.3.3. Methods for hive entrance sampling and DNA extraction

1.  In order to collect microorganisms stuck to the hive entrance or door, use sterile cotton swabs to scrub the surface. To maximize surface covering, the entrance should be swabbed by scrubbing left and right several times (~6) per swab tip (using 3 – 4 swabs per hive).

2.  Cut the heads of two cotton swab samples, deposit in a 2 mL tube, and add 800μl of PBS.

3.  Add 20 μl of protease and 400 μl of AL Buffer and vortex.

4.  Incubate at 56 ºC and 900 rpm for 1.5 hours.

5.  Transfer the liquid to a new tube (tube A) and add 20 μl of protease plus 400 μl of AL Buffer to the original tube (tube B).

6.  Incubate both tubes A and B at 56 °C and 900 rpm for 1.5 hours.

7.  Add 400 μl of 96-100% ethanol and vortex briefly (~15 seconds).

8.  Transfer the sample to the column (no more than 700 μl) and follow the established DNA extraction protocol, until eluting the DNA in 100 μl of buffer AE. **TIP:** Using a larger elution volume increases sample recovery.

9.  Store the DNA samples at ≤ -20 °C until ready for sequencing.
