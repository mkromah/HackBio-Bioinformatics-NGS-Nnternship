# HackBio-Bioinformatics-NGS-Internship
This repository contains projects and code from my internship in Bioinformatics and NGS Data Analysis. Includes Linux &amp; Bash scripting for bioinformatics pipelines, RNA sequencing (RNA-Seq) analysis, and whole genome sequencing (WGS) workflows with hands-on beginner-friendly implementations.
Great ✅ Here’s a **better structured README.md** with two separate sections (Project 1 & Project 2). You can copy this directly into your repo:
---

## 📂 Repository Structure

* `project.sh` → A Bash script combining **Project 1** and **Project 2** tasks.
* `README.md` → Documentation of the workflow.

---

# 🧪 Project 0: Bash Basics

### 🔹 Steps Implemented

1. **Print name**

```bash
echo "Musa"
```

2. **Create a folder with your name**

```bash
mkdir Musa_file
```

3. **Create a folder `biocomputing` and change to it in one line**

```bash
mkdir biocomputing && cd biocomputing
```

4. **Download 3 files**

```bash
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk   # duplicate
```

5. **Move `.fna` file into `Musa` folder**

```bash
mv *.fna ../Musa_file
```

6. **Delete duplicate `.gbk` file**

```bash
rm *.gbk.*
```

7. **Check if the `.fna` sequence is mutant (`tatatata`) or wildtype**

```bash
grep -i "tatatata" Musa_file/wildtype.fna
```

8. **If mutant, save lines to a file**

```bash
grep -i "tatatata" Musa/wildtype.fna | tr ' ' '\n' > Musa_file/mutant_lines.txt
```

9. **Count number of lines in `.gbk` file (excluding header)**

```bash
lines=$(wc -l biocomputing/wildtype.gbk | awk '{print $1}')
echo $((lines - 1))
```

10. **Print sequence length**

```bash
grep "LOCUS" biocomputing/wildtype.gbk | awk '{print $3}'
```

11. **Print source organism**

```bash
grep "SOURCE" biocomputing/wildtype.gbk | awk '{print $2, $3}'
```

12. **List all gene names**

```bash
grep "/gene=" biocomputing/wildtype.gbk | sed 's/\/gene=//'
```

13. **Clear terminal and list folder contents**

```bash
reset
ls Musa_file/ biocomputing/
```

---

# ⚙️ Project 1: Installing Bioinformatics Software

All installations were performed using **Conda**.

### 🔹 Steps Implemented

1. **Activate base environment**

```bash
conda activate base
```

2. **Create new environment**

```bash
conda create --name funtools
```

3. **Activate new environment**

```bash
conda activate funtools
```

4. **Install `figlet`**

```bash
conda install -c bioconda figlet
```

5. **Run `figlet` to print name in ASCII art**

```bash
figlet Musa
```

6. **Install essential bioinformatics tools**

```bash
conda install -c bioconda bwa
conda install -c bioconda blast
conda install -c bioconda samtools
conda install -c bioconda bedtools
conda install -c bioconda spades
conda install -c bioconda bcftools
conda install -c bioconda fastp
conda install -c bioconda multiqc
```

---

# ▶️ Usage

Clone the repo and run the script:

```bash
git clone https://github.com/mkromah/HackBio-Bioinformatics-NGS-Nnternship.git
cd HackBio-Bioinformatics-NGS-Nnternship
bash project.sh
```

---

# 👨‍💻 Author

**Musa Al Hassan Kromah**

* MSc Biotechnology | Çukurova University
* Passionate about **Bioinformatics & NGS Applications**
