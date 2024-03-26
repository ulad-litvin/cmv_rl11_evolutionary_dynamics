# cmv_rl11_evolutionary_dynamics

Python scripts and data to reproduce the results from Ulad Litvin, Eddie C.Y. Wang, Richard J. Stanton, Ceri A. Fielding, Joseph Hughes "Evolutionary Dynamics of the Cytomegalovirus RL11 Gene Family in Old World monkeys and Great Apes".

[ClipKit folder](clipkit)

Contains MAFFT and Foldseek protein alignments processed with ClipKit v.1.3.0 using:

```bash
clipkit al.fa -m smart-gap
```

[DIGS folder](digs)

Contains [raw DIGS results](digs/digs_raw_results.csv) and [processed DIGS results](digs/digs_processed_results_bitscore_46_length_75_one_hcmv.csv) generated with [DIGS notebook](notebooks/process_digs_results_manuscript.ipynb) and used to create the [Table S2](supplementary_tables/sup_table_2_digs_results_table.csv).

[ESMFold folder](esmfold)

Contains protein structures predicted with ESMFold v.1.0.3 using:

```bash
esm-fold -i ../fasta_files/adeno_cr1_cmv_rl11_elephantidbeta_ee50.fa -o ../esmfold/esmfold_adeno_cr1_cmv_rl11_pdbs
```

[FASTA files folder](fasta_files)

Contains FASTA files with sequences from the [Table S2](supplementary_tables/sup_table_2_digs_results_table.csv).

[Foldseek folder](foldseek)

Contains [Foldseek results](foldseek/foldseek_esmfold_cmv_rl11_with_rl11d_only_results.tsv) generated with Foldseek v.8.ef4e960 using:

```bash
foldseek createdb ../esmfold/esmfold_adeno_cr1_cmv_rl11_pdbs esmfold_pdbs_DB

foldseek easy-search ../esmfold/esmfold_adeno_cr1_cmv_rl11_pdbs esmfold_pdbs_DB foldseek/foldseek_esmfold_cmv_rl11_with_rl11d_only_results.tsv tmp --format-output "query,target,fident,alnlen,mismatch,gapopen,qstart,qend,tstart,tend,qaln,taln,evalue,bits,prob,lddt,alntmscore" --exhaustive-search -e 1
```

The [Foldseek results](foldseek/foldseek_esmfold_cmv_rl11_with_rl11d_only_results.tsv) were processed with [Foldseek notebook](notebooks/process_foldseek_results_manuscript.ipynb) to produce [Foldseek MSA](foldseek/al_foldseek_esmfold_mandrillinebeta1_RL11J.fa).

[GeneRax folder](generax)

Contains files produced with GeneRax v.2.0.4 using:

```bash
generax --families ../generax/rl11_family_file.txt --species-tree ../generax/cmv_tree.nw --rec-model UndatedDL --prefix ../generax/cmv_rl11_all_tbe_rec
```

[Functional regions prediction folder](interproscan_signalp_netnglyc_netoglyc)

Contains InterProScan 5, SignalP 6.0, NetNGlyc 1.0 and NetOGlyc 4.0 prediction results. These files were processed with [Domain prediction notebook](notebooks/process_domain_prediction_results.ipynb) to generate [Table S3](supplementary_tables/sup_table_3_digs_results_table_only_cmv_with_domains_coordinates.csv) and [RL11 structure figures](interproscan_signalp_netnglyc_netoglyc/figures).

[IQTREE folder](iqtree)

Contains ML phylogenies generated from [ClipKit processed alignments](clipkit) with IQTREE v.2.1.3 using:

```bash
iqtree2 -s clipkit_al.fa -b 100 --tbe
```
[MAFFT folder](mafft)

Contains multiple sequence alignment files generated from [FASTA files](fasta_files) with MAFFT v.7.475 using:

```bash
mafft --auto --reorder fasta.fa > al.fa
```

[Notebooks folder](notebooks)

Contains Jyputer notebooks with Python scripts to process [DIGS results](digs), [Foldseek results](foldseek) and [Functional regions prediction results](interproscan_signalp_netnglyc_netoglyc).

[Supplementary tables folder](supplementary_tables)

Contains [Table S1](supplementary_tables/sup_table_1_digs_genomes_table.csv) with genomes used for DIGS screening, [Table S2](supplementary_tables/sup_table_2_digs_results_table.csv) with processed DIGS results, [Table S3](supplementary_tables/sup_table_3_digs_results_table_only_cmv_with_domains_coordinates.csv) with annotation of functional regions.