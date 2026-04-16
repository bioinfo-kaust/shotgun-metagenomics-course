# Shotgun Metagenomics: From Raw Reads to MAGs

**KAUST Bioinformatics Platform — 4-Day Workshop**

A hands-on course covering every stage of shotgun metagenomics analysis, from raw read QC through to a complete automated run with nf-core/mag. Participants run each tool manually first, then see how the full pipeline ties it all together.

🌐 **Course website:** https://bioinfo-kaust.github.io/shotgun-metagenomics-course/

---

## Course Structure

| Session | Topic |
|---------|-------|
| Day 1 Lab | Linux Command Line & Ibex Cluster |
| Day 1 Lab | Nextflow & nf-core/mag Overview |
| Module 1 | QC & Preprocessing |
| Module 2 | Assembly, Evaluation & Annotation |
| Module 3 | Ancient DNA Analysis |
| Module 4 | Contig Binning |
| Module 5 | Bin Refinement |
| Module 6 | Bin Quality Evaluation |
| Module 7 | Taxonomy & Annotation |
| Module 8 | Run Summary & nf-core/mag |

## Prerequisites

- Basic Linux command line skills
- Familiarity with NGS concepts (FASTQ format, paired-end reads)
- KAUST Ibex HPC account ([request access](https://my.ibex.kaust.edu.sa))

## Tools Covered

FastQC · fastp · Bowtie2 · BBNorm · NanoPlot · Porechop_ABI · Chopper · Filtlong · Nanoq · MEGAHIT · metaSPAdes · Flye · metaMDBG · QUAST · ALE · Prodigal · geNomad · PyDamage · FreeBayes · BCFtools · MetaBAT2 · MaxBin2 · CONCOCT · COMEBin · MetaBinner · SemiBin2 · Tiara · DAS Tool · CheckM2 · BUSCO · GUNC · GTDB-Tk · CAT · Prokka · MetaEuk · MultiQC · BigMAG · Nextflow · nf-core/mag

## Instructors

- **Salim Bougouffa** — Senior Computational Biologist, KAUST CBRC & Bioinformatics Platform
- **Husen M. Umer** — Bioinformatics Staff Scientist, KAUST Bioinformatics Platform
- **Ikram Ullah** — Staff Scientist, KAUST Biosciences Core Laboratory
- **Issaac Rajan** — Bioinformatics Staff Scientist, KAUST Bioinformatics Platform

## Deployment

The site is built as plain HTML/CSS and deployed automatically to GitHub Pages via GitHub Actions on every push to `main`.

To preview locally:
```bash
python3 -m http.server 8000
# Open http://localhost:8000
```

## License

Course materials are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt with appropriate attribution.

© 2026 KAUST Bioinformatics Platform
