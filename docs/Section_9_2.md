# 9. Metabolomics

## 9.2. Sample preparation for metabolomics

### 9.2.1. Considerations

#### 9.2.1.1 General

-   Metabolomics experiments may be either focused on discovery (untargeted analysis; e.g. discovery of metabolome changes in response to stimuli) or monitoring changes in or presence of an *a priori* defined set of compounds (targeted analysis). This protocol may need to be adjusted if the analytes of interest are better extracted in another solvent or better separated with another LC gradient.

-   Untargeted metabolomics analysis is normally conducted using high-resolution instruments such as Q-TOF or Orbitrap mass spectrometers while targeted metabolomics may be performed with low resolution, highly selective mass spectrometers such as triple quadrupoles (QQQs). Ensure the instrumentation available meets the needs of your experiment and sample complexity

-   Mass spectrometer sensitivity may drift between runs. Running QCs every few samples is thus useful for data normalization. Constitute quality control (QC) samples by mixing equal volumes from all samples.

-   Data acquisition can be performed in both positive and negative ion mode, and small molecules may be more amenable to one or the other depending on their structure and functional groups. Though time consuming, analyzing samples in both negative and positive ionization modes captures a wider spectrum of metabolites.

-   Aim to inject 1-10 µl of sample into the column. Before running a batch of new samples, check the concentrations by running a diluted test sample. This will help gauge the amount to inject to avoid overloading or underloading the instrument.

-   Adding a generic internal standard during sample preparation can help the user compare data between sample runs and facilitate relative quantitation. However, for absolute quantitation, either isotopically-labeled internal standards matching the compound of interest or external standard curves of the unlabelled compound are required.

#### 9.2.1.2. Sample handling

-   Store samples at -80 °C

-   Sample processing is somewhat dependent on the type of metabolite to be extracted and identified. Generally, methanol:water extractions work well, but the extraction solvent may need to be adjusted to best capture specific classes of compounds (see Section 9.1).

-   The step at which an internal standard is added may vary. Adding the standard before homogenization accounts for variation in extraction efficiency, while adding the standard immediately ahead of injection will ensure the same amount is present in each sample. If desired, two sets of internal standards may be added at different points in the sample processing protocol.

-   Blank samples should be prepared in parallel with real samples in order to determine what compounds are contaminants introduced from solvents, plastics, and the environment. These blank samples should be analyzed at regular intervals during data acquisition and it is good practice to either subtract the average intensities of compounds in the blank samples from those in real samples, or to only retain sample compounds present at an abundance above a threshold factor over the blanks (e.g. 5-fold higher in real samples than blanks)

-   Solvent-only injections may also be performed at regular intervals in order to assess sample carry-over between injections as well as potential system contamination. These injections are distinct from blank samples in that they are not derived from parallel processing of real samples; instead, they are comprised of pure reconstitution buffer

-   LC-MS/MS instruments with auto-samplers require HPLC vials (~ 2 mL). For small volume samples, a 300 µl vial insert may be required.

#### 9.2.1.3. Reagent handling

-   All reagents and solvents should be mass spectrometry grade. Care must be taken to avoid any impurities in the reagents and chemicals used.

-   Prepare fresh buffers and solutions.

### 9.2.2. Materials

-   Large equipment: homogenizer or bead beater, centrifuge, speed vacuum concentrator, -80 °C and -20 °C freezers, a vortex, and liquid chromatography system coupled to a mass spectrometer (for example, a high-resolution system such as a Nexera LC30 UPLC (Shimadzu) coupled to a quadrupole-time-of-flight mass spectrometer (TripleTOF 5600, AB SCIEX), but see [Section 9.3]{.underline})

-   In-house library of metabolites (such as the IROA Mass Spectrometry Metabolite Library of Standards)

-   Mass spectrometry grade methanol, water, formic acid, and acetonitrile

-   Homogenization tubes and beads

### 9.2.3. Metabolomics methods

#### 9.2.3.1. Sample homogenization

1.  Homogenize 50 mg of sample in 0.5 ml of methanol and water solution (80:20 v/v) in a homogenizer (for example, a *QIAGEN* TissueLyser or Precellys 24 tissue homogenizer). Use tubes and tips without color. **TIP:** Including BHT (butylated hydroxytoluene) at 0.01% in the extraction solvent protects compounds from oxidation

2.  Homogenize until the tissues are broken down into minute particles to maximize extraction.

#### 9.2.3.2. Extraction

3.  Incubate samples for at least 1 hour at -20 °C to allow metabolites to be extracted and proteins to precipitate.

4.  Centrifuge at 10,000 g for 10 min (4 °C) to pellet the precipitate containing proteins and other cellular debris.

5.  Transfer 400 µl of the supernatant to a clean 2 ml tube and evaporate to dryness in a speed vacuum concentrator.

6.  Reconstitute dry extracts in 200 µl of acetonitrile:water solution (1:1 v/v).

7.  Vortex the tube for 30 s and centrifuge for 10 min at 10,000 g (4 °C).

8.  Collect the supernatants and transfer them to HPLC vials.

9.  If not immediately conducting mass spectrometry, store the samples at -80 °C until analysis. Re-centrifuge the samples before LC-MS/MS to remove any precipitates.
