#  Steps and Usage Guidelines of Montreal Forced Aligner (MFA)

This guide explains how to set up, run, and verify **Montreal Forced Aligner (MFA)** for speech-text alignment, and how to visualize the results using **Praat**.

---

##  1. Create and Activate Environment

```bash
conda create -n mfa_env -c conda-forge montreal-forced-aligner -y # Create a new environment and install MFA
conda activate mfa_env # Activating mfa_environmkent
```

---

##  2. Check Installation

```bash
mfa version # Verify the installation
```

---

##  3. Download Models 

```bash

mfa model download dictionary english_us_arpa # Download English dictionary
mfa model download acoustic english_us_arpa # Download English acoustic models
```

---

##  4. Validate Dataset

```bash
mfa validate "C:\Users\ramra\OneDrive\Desktop\MFA_Assignment" english_us_arpa english_us_arpa # Validate your dataset before alignment
```

**Notes:**
- Your corpus should have this structure:
  ```
  corpus/
  ├── wav/
  │   ├── file1.wav
  │   ├── file2.wav
  └── transcripts/
      ├── file1.txt
      ├── file2.txt
  ```

---

##  5. Run Forced Alignment

```bash
# Perform forced alignment and clean temporary files after completion
(aligner) C:\Users\ramra\OneDrive\Desktop\MFA_Assignment>mfa align mfa_corpus english_us_arpa english_us_arpa mfa_output --clean
```

**Output:**
- MFA will generate `.TextGrid` files in your output directory.
- Each TextGrid file corresponds to a `.wav` file with word and phoneme alignment.

---

##  6. View Alignments in Praat

Once the alignment is complete, you can visualize the results using **Praat**.

### Steps:
1. Open **Praat**.
2. Go to **Open → Read from file...**
3. Load the aligned `.TextGrid` file (e.g., `F2BJRLP1.TextGrid`).
4. Load the matching `.wav` file (e.g., `F2BJRLP1.wav`).
5. In the **Praat Objects** window:
   - Select both the **Sound** and **TextGrid** objects.
   - Click **View & Edit**.
6. The waveform and alignment tiers (Words, Phonemes) will appear.
   - You can zoom, play, and inspect the alignment boundaries.
   - Use **View → Show Analyses** for additional visual layers.

---

##  Example Output

Each TextGrid includes:
- **Words tier:** aligned word boundaries  
- **Phonemes tier:** time-aligned phoneme segments  
- Minor timing differences (~0.06–0.2 sec) are normal due to natural speech variations.

---

##  Summary

The Montreal Forced Aligner combines:
- **Acoustic Models** (speech-to-phoneme mapping)  
- **Pronunciation Dictionaries** (word-to-phoneme mapping)  
- **Forced Alignment Algorithms**

Together, they produce accurate word and phoneme alignment from audio–text pairs.

---

###  Example Directory Structure

```
Assignment/
├── corpus/
│   ├── wav/
│   │   ├── F2BJRLP1.wav
│   │   ├── F2BJRLP2.wav
│   └── transcripts/
│       ├── F2BJRLP1.txt
│       ├── F2BJRLP2.txt
├── output/
│   ├── F2BJRLP1.TextGrid
│   ├── F2BJRLP2.TextGrid
└── README.md
```

---

**Author:** V.ARTHI ANVITHA REDDY 
**Environment:** `mfa_env` (Montreal Forced Aligner)  
**Tools:** MFA, Praat, Conda  
