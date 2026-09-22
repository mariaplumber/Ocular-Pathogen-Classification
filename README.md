Data

studydesign.xlsx contains the sample metadata. Bulk RNA-seq data were retrieved from the NCBI Sequence Read Archive (Homo sapiens, transcriptomic, cDNA selection) and pseudoaligned to the Ensembl human transcriptome.

The data folder holds one Excel file per sample, in per-pathogen subfolders (HHV1, HCMV5, Asper, Cand, Myc, Pseu), named Pathogen_Condition_SampleID_BioProject_CellType.xlsx. 330 samples are included (177 infected, 153 mock). Transcript abundances are aggregated to gene level by summation across isoforms using tx2gene.tsv.

PRJNA388483 and PRJNA494846 each contain two host cell types and were split by cell type into separate analysis units, giving 38 units from 36 BioProjects. Cell types in studydesign.xlsx are recorded at a general level; the specific cell line is given in each file name.

Code
01_per_pathogen_deseq2.ipynb is gene-level aggregation, filtering, per-study differential expression (PyDESeq2), robust-gene selection, per-pathogen PCA.
02_classification.ipynb is combined log fold-change matrix, UMAP, supervised classification with cross-study validation.

Cell outputs are retained. File paths are absolute and machine-specific so update the paths at the top of each notebook before running.

Outputs

combined_lfc_matrix.tsv (per-sample log₂ fold change relative to study-matched mock, robust genes only), the six per-pathogen robust gene lists, and gene_selection_frequency_60_across_folds.csv (142 genes selected across cross-validation folds).

Requirements

Python 3.13.5; Key packages: pydeseq2, scikit-learn, umap-learn, pandas, numpy
