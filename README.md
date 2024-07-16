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
- Good luck with your analyses!

[Open in Google Colab](https://colab.research.google.com/drive/1ZJM2iefEgxJp0mZUsDZZteBQL0Zd4L_r?usp=sharing)
