# Genome-Analysis
Genome Analysis Project

**Project Plan**

**Aim:**
"Dead Zones" or areas of ocean with seasonal to long-term low dissolved oxygen (DO) concentrations are becoming increasingly more frequent. This study focuses on one of the largest costal dead zones on the northern Gulf of Mexico. The low DO levels are due to eutrophication-enhanced bacterioplankton respiration as well as strong seasonal stratification. I am going to assemble genomes of becterioplankton collected from the northern Gulf of Mexico dead zone by Thrash et al. as described in *Metabolic roles of uncultivated bacterioplankton lineages in the Northern Gulf of Mexico “dead zone”*. 
     

**Workflow**

![HI](https://github.com/torigiffin/Genome-Analysis/assets/128710633/a7e8a505-2349-42b0-a45c-fde85e48068d)


| Analysis | Program | Output | Expected Run Time | Expected Deadline | Completed
| ---         |     ---      |          --- |     ---      | ---      | ---      |
| Reads Quality Control | FastQC    | .html |   ~15 min    | April 7th    | Yes    |
| RNA Trimming   | Trimmomatic   | fastq |   ~30 min    | April 7th    | Yes    |
| DNA Assembly   | Megahit  | <ul><li>./megahit_out with output directory</li><li>.contigs.fa with contigs</li></ul>  | ~6 h     | April 7th   | Yes |
| Assembly Evaluation   | QUAST  | <ul><li>.txt</li><li>.pdf</li></ul>  | ~ 45 min    | April 14th   | Yes |
| DNA Alignment  | BWA    | .bam | ~ 4-6 h    | April 21st    | Yes |
| Binning | Metabat  |  .fasta for each bin | <30 min    | April 21st    | Yes |
| Binning Evaluation  | CheckM |  output report | ~2 h    | April 21st   | Yes |
| RNA Alignment  | BWA    | .sam | ~ 4-6 h    | April 21st    | Yes |
| Annotation   | Prokka  | <ul><li>GFF file with annotations</li><li>GenBank file with sequences</li></ul> | ~ 1 h   | April 28th    |  Yes |
| Phylogenetic Placement   | PhyloPhlan |  <ul><li>top SGBs</li><li>closest SGB, GGB, FGB</li><li>reference genomes, and "all vs. all" matrix of all pairwise Mash distances</li></ul>  | ~6 h  | April 28th    | Yes |
| Expression Analysis   | HTseq  |  .txt with read count table   | ~6 h    | April 28th   | Yes |
| Extra Analysis: Abundance of Organisms | BWA | .bam | ~ 4-6 h | May 12th |


**Data Management System**
<pre>
├── genome_analyses
    ├── 01_reads_quality_control  
    │       └── fastqc_trimmed_RNA_script 
    │       └── slurm-7528571.out 
    │   ├── fastqc_DNA_results
    │   ├── fastqc_RNA_post_trim_results
    │   ├── fastqc_RNA_pre_trim_results
    ├── 02_RNA_trimming
    │       └── adapter_sequences
    │       └── slurm-7528563.out
    │       └── trimmomatic_script
    │   ├── trimmed_RNA
    ├── 03_DNA_assembly
    │       └── megahit_script
    │       └── slurm-7723214.out
    │   ├── DNA_assembly_results
    ├── 04_assembly_evaluation 
    │       └── quast_script
    │       └── slurm-7731177.out
    │   ├── quast_results 
    ├── 05_alignment
    │       └── bwa_results_SRR4342129.bam
    │       └── bwa_results_SRR4342133.bam
    │       └── bwa_script
    │       └── slurm-7795240.out
    ├── 06_binning
    │       └── change_bin_names_script
    │       └── depth.txt
    │       └── metabat_script
    │       └── slurm-7797909.out
    │       └── slurm-7799427.out
    │   ├── bins
    ├── 07_binning_evaluation
    │       └── checkm_qa
    │       └── checkm_qa_script
    │       └── checkm_script
    │       └── slurm-7799916.out
    │       └── slurm-7827270.out
    │   ├── CheckM_data
    │   ├── checkm_results
    ├── 08_RNA_mapping
    │       └── 1_SRR4342137_RNA_alignment.bam
    │       └── ...
    │       └── 49_SRR4342139_RNA_alignment.bam
    │       └── bwa_script_for_loop 
    │       └── bwa_script_for_loop_sample_2
    │       └── slurm-7855951.out
    │       └── slurm-7855966.out
    ├── 09_annotation
    │       └── prokka_script
    │       └── rename_annotation
    │       └── slurm-7852786.out
    │   ├── 1_prokka_results 
    │   ├── ...  
    │   ├── 49_prokka_results  
    │   ├── renamed_annotations  
    ├── 10_phylo_placement
    │       └── make_annotation_folder 
    │       └── phylophlan_conda_script
    │       └── slurm-7856958.out
    │   ├── phylogeny_results  
    ├── 11_expression_analysis
    │       └── 1_SRR4342137_expression_results.txt
    │       └── ...
    │       └── 49_SRR4342139_expression_results.txt
    │       └── htseq_script
    │       └── slurm-7856869.out
    ├── DNA_trimmed
    ├── RNA_untrimmed
</pre>
