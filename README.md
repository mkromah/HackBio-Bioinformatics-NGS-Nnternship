# HackBio Bioinformatics & NGS Internship Projects

This repository contains projects and code from my internship in Bioinformatics and Next-Generation Sequencing (NGS) Data Analysis. It demonstrates hands-on, beginner-friendly implementations for Linux & Bash scripting, RNA sequencing (RNA-Seq) analysis, and whole genome sequencing (WGS) workflows.

---

## 📂 Repository Structure

| File/Folder | Description |
|-------------|-------------|
| `project.sh` | A Bash script combining Project 0, Project 1, and the S. aureus RNA-Seq analysis workflow. |
| `README.md` | This documentation detailing workflows, projects, and usage instructions. |
| `01_download_data.sh` | Bash script to download raw RNA-Seq FASTQ files for S. aureus PJI study. |
| `02_qc_and_trim.sh` | Run FastQC and Fastp for quality control and trimming. |
| `03_alignment.sh` | Align reads to the S. aureus reference genome using HISAT2. |
| `04_feature_count.sh` | Count reads per gene using featureCounts. |
| `05_DE_analysis.R` | Perform DESeq2 differential expression analysis, PCA, volcano plots, and heatmaps. |
| `06_pathway_enrichment.R` | Functional enrichment (GO/KEGG) and pathway visualization. |
| `environment.yml` | Conda environment file to ensure reproducibility (tools + R packages). |

---

## 🧪 Project 0: Bash Basics

**Steps Implemented:**

- Print name:
  ```bash
  echo "Musa"
````

* Create a folder with your name:

  ```bash
  mkdir Musa_file
  ```
* Create a folder `biocomputing` and change into it:

  ```bash
  mkdir biocomputing && cd biocomputing
  ```
* Download 3 files:

  ```bash
  wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna
  wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
  wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk   # duplicate
  ```
* Move `.fna` file into Musa folder:

  ```bash
  mv *.fna ../Musa_file
  ```
* Delete duplicate `.gbk` file:

  ```bash
  rm *.gbk.*
  ```
* Check if the `.fna` sequence is mutant (`tatatata`) or wildtype:

  ```bash
  grep -i "tatatata" Musa_file/wildtype.fna
  ```
* If mutant, save lines to a file:

  ```bash
  grep -i "tatatata" Musa_file/wildtype.fna | tr ' ' '\n' > Musa_file/mutant_lines.txt
  ```
* Count number of lines in `.gbk` file (excluding header):

  ```bash
  lines=$(wc -l biocomputing/wildtype.gbk | awk '{print $1}')
  echo $((lines - 1))
  ```
* Print sequence length:

  ```bash
  grep "LOCUS" biocomputing/wildtype.gbk | awk '{print $3}'
  ```
* Print source organism:

  ```bash
  grep "SOURCE" biocomputing/wildtype.gbk | awk '{print $2, $3}'
  ```
* List all gene names:

  ```bash
  grep "/gene=" biocomputing/wildtype.gbk | sed 's/\/gene=//'
  ```
* Clear terminal and list folder contents:

  ```bash
  reset
  ls Musa_file/ biocomputing/
  ```

---

## ⚙️ Project 1: Installing Bioinformatics Software

All installations were performed using Conda.

**Steps Implemented:**

```bash
# Activate base environment
conda activate base

# Create new environment
conda create --name funtools

# Activate new environment
conda activate funtools

# Install figlet
conda install -c bioconda figlet
figlet Musa

# Install essential bioinformatics tools
conda install -c bioconda bwa blast samtools bedtools spades bcftools fastp multiqc
```

---

## 🧬 Project 2: Transcriptomic Profiling of *Staphylococcus aureus* in PJI

**Objective:**
Analyze RNA-Seq data to identify differential gene expression, virulence factors, and functional pathways between acute and chronic phases of periprosthetic joint infections (PJI).

**Workflow Steps:**

1. **Download Data**

   ```bash
   bash 01_download_data.sh
   ```
2. **Quality Control & Trimming**

   ```bash
   bash 02_qc_and_trim.sh
   ```
3. **Alignment to Reference Genome**

   ```bash
   bash 03_alignment.sh
   ```
4. **Feature Counting**

   ```bash
   bash 04_feature_count.sh
   ```
5. **Differential Expression Analysis**

   ```R
   # 05_DE_analysis.R
   ```
6. **Pathway Enrichment & Functional Analysis**

   ```R
   # 06_pathway_enrichment.R
   ```

**Highlights:**

* Separation of acute vs chronic infection samples.
* PCA and heatmap visualizations of key DEGs.
* Identification of virulence, stress response, and metabolic pathways.
* GO/KEGG enrichment for functional insights.
* RNA regulatory elements exploration.

---

## ▶️ Usage

Clone the repository and run the scripts in order:

```bash
git clone https://github.com/mkromah/HackBio-Bioinformatics-Intership.git
cd HackBio-Bioinformatics-Intership
bash project.sh
```

---

## 👨‍💻 Author

**Musa Al Hassan Kromah**
MSc Biotechnology | Çukurova University
Passionate about Bioinformatics & NGS Applications
