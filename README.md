# qpAdm_on_Colab

## References:
1. [AdmixTools on GitHub](https://github.com/DReichLab/AdmixTools/tree/master)
2. [Allen Ancient DNA Resource](https://reich.hms.harvard.edu/allen-ancient-dna-resource-aadr-downloadable-genotypes-present-day-and-ancient-dna-data)
3. [PLINK 1.9 Input Files](https://www.cog-genomics.org/plink/1.9/input#23file)
4. Add more references as needed.

## Using LivingDNA Data with qpAdm_on_Colab
If you have LivingDNA data, you can replace the headers from 23andme files and convert them to bed format using the following command:
```bash
plink --23file <filename> [family ID] [within-family ID] [sex] [phenotype] [paternal ID] [maternal ID] --out plink_genome
```
For example:
```bash
plink --23file genome.txt Chang Christopher --out plink_genome
```

## Usage Notes:
- Ensure that AdmixTools is installed in the `src` folder, and execute all commands within the `bin` folder (recommended).
- Always verify the current directory you are working in.
- Follow the steps sequentially on Colab.
- If you find this helpful, consider liking and following me for more updates.
  
[Open in Google Colab](https://colab.research.google.com/drive/1ZJM2iefEgxJp0mZUsDZZteBQL0Zd4L_r?usp=sharing)

# Detailed explanations for each step:

### Step 1: Install Dependencies and Download AdmixTools

1. **Update and Install Packages:**
   - `sudo apt-get update`: Updates package lists for upgrades.
   - `sudo apt-get install wget unzip`: Installs wget and unzip utilities for downloading and extracting files.
   
2. **Download and Extract AdmixTools:**
   - `wget https://github.com/DReichLab/AdmixTools/archive/master.zip -O AdmixTools.zip`: Downloads AdmixTools from GitHub.
   - `unzip AdmixTools.zip`: Unzips the downloaded file to extract AdmixTools.

### Step 2: Compile AdmixTools

3. **Navigate to Source Directory and Install Dependencies:**
   - `cd AdmixTools-master/src`: Moves to the source directory of AdmixTools.
   - `sudo apt-get install build-essential libgsl-dev libopenblas-dev`: Installs necessary build tools and libraries (GSL and OpenBLAS).
   
4. **Compile AdmixTools:**
   - `make clobber`: Cleans any existing compiled binaries.
   - `make all`: Compiles all necessary binaries.
   - `make install`: Installs the compiled binaries.

### Step 3: Prepare Dataset

5. **Download and Extract Dataset:**
   - Downloads a dataset (`v54.1.p1_1240K_public.tar`) and extracts it.

6. **Organize Dataset:**
   - Creates a new directory (`/content/AdmixTools-master/bin/dataset`) and moves necessary dataset files (`v54.1.p1_1240K_public.*`) into it.

### Step 4: Run Analysis Using qpAdm

7. **Run `qpAdm`:**
   - Executes `qpAdm` from `/content/AdmixTools-master/bin/qpAdm` to perform admixture analysis.

### Step 5: Prepare PLINK and Genetic Data

8. **Install PLINK and Prepare Genetic Data:**
   - Installs PLINK (a tool for genetic analysis) and prepares genetic data (`genome.txt`).

### Step 6: Convert Genetic Data Format

9. **Convert Genetic Data Format:**
   - Uses `convertf` to convert genetic data format based on parameters in `convertf_param.par`.

### Step 7: Merge Datasets

10. **Merge Datasets Using `mergeit`:**
    - Merges datasets using parameters in `merge_param.par` with `mergeit`.

### Step 8: Modify Metadata

11. **Modify Metadata (`Yusup_merged_with_1240K.ind`):**
    - Modifies the last line of metadata to include personal information (name and gender).

### Step 9: Create Additional Folders

12. **Create Additional Folders:**
    - Creates folders (`fstat_genome` and `fstat_ancestry`) within `/content/AdmixTools-master/bin` for storing results.

### Step 10: Prepare F-Statistics Analysis

13. **Prepare F-Statistics Analysis:**
    - Creates configuration files (`parqpfstat.txt` and `lista.txt`) for running `qpfstats` in both `fstat_genome` and `fstat_ancestry`.

### Step 11: Run F-Statistics Analysis

14. **Run F-Statistics Analysis:**
    - Executes `qpfstats` to compute F-statistics based on the prepared configuration files.

### Step 12: Verify and Print Results

15. **Verify and Print Results:**
    - Reads and prints the last few lines of important files (`Yusup_merged_with_1240K.ind` and `fstat_genome/fstatsa.txt`) to verify operations and view results.
