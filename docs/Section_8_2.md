# 8. Proteomics

## 8.2. Standard methods for shot-gun proteomics sample preparation

### 8.2.1. Considerations

#### 8.2.1.1. General

-   Depending on the type of tissue, expect between 1 and 10% of the total wet mass to be made up of protein.

-   Aim to digest 10-30 µg of protein per sample – more if performing additional sample enrichment or fractionation steps (*e.g.* high-pH reverse phase fractionation, phosphopeptide enrichment, size exclusion chromatography, *etc*) ahead of LC-MS/MS (reviewed elsewhere (Hedrick et al., 2015)).

-   Mass spectrometer and liquid chromatography parameters are reviewed elsewhere (Savaryn et al., 2016).

#### 8.2.1.2. Sample handling

-   Always use gloves and keep the workspace free from dust to prevent keratin contamination. Do not wear wool clothing.

-   Adult honey bees and larvae can be coated with unwanted substances (*e.g.* honey, pollen, or royal jelly). Wash the samples by gently vortexing one or more times in phosphate-buffered saline (1x PBS) prior to lysis to help remove contaminants.

-   If preparing fatty tissue samples, such as fat bodies, avoid retaining the top layer of fat after clarifying the lysate.

-   If preparing gut samples, consider that there could be many plant, fungal, and bacterial proteins present inside. These could be washed out or included in the analysis, depending on the purpose of the experiment. But, if included, their protein sequences must be added to the search database in order to identify them.

-   Guanidinium chloride will denature enzymes and must be removed from the sample or diluted prior to digestion. Protease inhibitors are not necessary during sample lysis if using a guanidinium chloride extraction buffer, but may be considered if a non-denaturing buffer is used.

-   Mass spectrometry is not compatible with polymers (*e.g.,* polyethylene glycol, PEG) and detergents (*e.g.,* sodium dodecyl sulfate, SDS). If such reagents come in contact with the sample, they must be removed prior to mass spectrometry analysis. Consult Keller *et al.* (2008) for a list of common contaminants.

-   Mass spectrometry data analysis is not compatible with disulfide bonds between peptides. Disulfide bonds must therefore be reduced and alkylated to block the reactive sulfur.

#### 8.2.1.3. Reagent handling

-   All reagents should be mass spectrometry grade.

-   When preparing reagents with undiluted strong acids, use glass pipettes for dispensing, as polymers and plasticizers can leach from plastics in contact with strong acids.

### 8.2.2. Materials

-   Large equipment: sample homogenizer (*e.g.* Precellys 24), speed-vac, centrifuge, bath sonicator (optional), liquid chromatography system coupled to a mass spectrometer (see [Section 8.3](https://maevatecher.github.io/standard-methods-apis-omics/Section_8_3/) for more details)

-   Homogenization tubes (*e.g.* 2 mL DuraTubes) and ceramic homogenization beads

-   C18 membrane or inert material for a column frit

-   Bulk C18 powder (*e.g.* ReproSil-Pur 120 C18-AQ, 2.4 µm)

-   Lysis buffer (6 M guanidinium chloride, 100 mM Tris, pH 8.0) – store at room temperature (RT) for several days, or 4 °C for weeks or months

-   100% acetone (pre-chilled to -20 °C)

-   80% acetone in water (pre-chilled to -20 °C)

-   Bradford assay reagents (store at 4 °C)

-   Step 1 digestion buffer (6 M urea, 2 M thiourea, 100 mM Tris, pH 8.0) – make fresh

-   Step 2 digestion buffer (50 mM ammonium bicarbonate, pH 8.0) – make fresh

-   Endoproteinase lys-C, mass spectrometry grade (see manufacturer’s protocol for storage)

-   Porcine-modified trypsin, mass spectrometry grade (see manufacturer’s protocol for storage)

-   Dithiothreitol (DTT; 0.5 µg/µl in water) – store at -20 °C

-   Iodoacetamide (IAA; 1 µg/µl in water) – store at -20 °C, sensitive to light

-   Buffer A (0.2% trifluoroacetic acid in water) – store at RT

-   Buffer B (0.1% formic acid, 80% acetonitrile in water) – store at RT

-   Elution buffer (0.1% formic acid, 40% acetonitrile in water) – store at RT

-   Resuspension buffer (0.1% formic acid, 2% acetonitrile in water – store at RT

### 8.2.3. Proteomics methods

#### 8.2.3.1. Lysis and precipitation

1.  Place the tissue sample (1 – 100 mg) in a homogenization tube with four ceramic beads and cold lysis buffer (maximum ratio: 100 mg tissue per mL). Work on ice.

2.  Homogenize the sample (3 x 30 s, 1 min on ice in between, maximum frequency 6,000 rpm).

    **TIP:** The sample should be pulverized with no large pieces left in the solution. If you do not have a bead mill homogenizer and have a large sample quantity, the sample can be ground in liquid nitrogen with a mortar and pestle, then transferred to a tube containing lysis buffer.

3.  Quick spin, then transfer lysate to a new tube. Spin sample at 16,000 *g* for 10 min (4 °C) to remove debris. Transfer supernatant to a new tube. Repeat if necessary.

4.  Precipitate protein from the clarified lysate by adding 4x the sample volume of ice-cold 100% acetone (-20 °C, overnight - final solution should be 80% acetone).

5.  Spin sample at 5,000 *g* (15 min, 4 °C) to pellet precipitated protein. Discard the supernatant and wash the pellet with 500 µl ice-cold 80% acetone. For large pellets, disrupt with the pipet tip or sonicator for complete washing. Repeat, spin again, and discard the final supernatant.

6.  Allow residual acetone to air dry until the tube is odorless (~5 min, RT). **TIP:** Careful not to over-dry or the pellet will be difficult to resuspend.

#### 8.2.3.2. Solubilization and digestion

7.  Solubilize the pellet in step 1 digestion buffer. **TIP:** Do not heat samples in urea. If the pellet is difficult to solubilize, sonicate in an ice water bath instead.
8.  Estimate protein concentration using a Bradford assay.
9.  Reduce disulfide bonds by adding 1 µg DTT per 50 µg protein, incubate at RT, 30 min.
10. Alkylate cysteine residues by adding 5 µg IAA per 50 µg protein, incubate at RT, 20 min. **TIP:** IAA is light-sensitive – keep the reaction and reagents in the dark.
11. Digest protein by adding 1 µg lys-C per 50 µg protein, incubate at RT, 3 h, dark.
12. Dilute the mixture with six volumes of step 2 digestion buffer and add 1 µg trypsin per 50 µg protein, incubate at RT at least 4 h (up to overnight), dark.
13. When complete, acidify the peptide digest to pH < 2.0 using 20% formic acid diluted in water. Check pH by dispensing a small amount (~0.2 μl) onto a pH test strip.

#### 8.2.3.3. Peptide desalting and resuspension

14. Prepare desalting ‘columns’ (Rappsilber et al., 2003) by punching out small disks of C18 Empore filter using a 17 G flat-tipped syringe and ejecting the disks into P200 pipette tips. Ensure that the disk is securely wedged in the bottom of the tip. Stack bulk C18 powder above the disk by suspending the powder in methanol and pipetting it into the tip. Elute the methanol either by centrifugation or by pressurizing the tip with a syringe barrel. The C18 stack should be ~1 cm tall and can desalt a sample containing ~50 µg of peptides, although capacity may vary depending on the type of bulk C18 material used.
15. Wash the column with 200 µl Buffer B. Discard eluate. If any C18 columns have visible channels or dead volume after this stage, do not use the column.
16. Condition the column with 200 µl Buffer A. Discard eluate.
17. Load the column with the peptide digest sample. Discard eluate.
18. Wash the column at least twice with 200 µl Buffer A. Discard eluate.
19. Elute peptides into a clean tube with 200 µl elution buffer. Repeat for complete elution (expect one elution to yield ~90% of peptides).
20. Evaporate the sample in a vacuum centrifuge (RT) until dry.
21. Dissolve peptides in resuspension buffer and quantify by nanodrop. Equalize the sample concentrations. TIP: If an absorbance peak is observed at 240 nm, this likely indicates residual urea/thiourea contamination. The sample may need to be desalted again
22. Centrifuge diluted samples at 16,000 g (10 min) to remove potential particulates from solution. Transfer the supernatants in randomized order to a 96-well autosampler plate for LC-MS/MS.
