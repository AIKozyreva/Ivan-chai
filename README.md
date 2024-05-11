# Ivan-chai
ivan-chai data by QIIME2 for Ivan

Raw data: /mnt/SSD4TB/STORAGE/240412_MGI_ITS

my Project folder: /mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion 

## QIIME2 + DADA2 + pretrained NaiveBayes + Unite db (UNiref97-99 for all euk version for 2023.2)

### Import data
Manifest file is: /mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/manifest.tmp
```
sample-id	forward-absolute-filepath	reverse-absolute-filepath
sample-100	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_100_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_100_2.fq.gz
sample-101	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_101_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_101_2.fq.gz
sample-102  /mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_102_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_102_2.fq.gz
sample-89	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_89_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_89_2.fq.gz
sample-90	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_90_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_90_2.fq.gz
sample-91	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_91_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_91_2.fq.gz
sample-92	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_92_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_92_2.fq.gz
sample-93	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_93_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_93_2.fq.gz
sample-94	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_94_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_94_2.fq.gz
sample-95	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_95_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_95_2.fq.gz
sample-96	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_96_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_96_2.fq.gz
sample-97	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_97_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_97_2.fq.gz
sample-98	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_98_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_98_2.fq.gz
sample-99	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_99_1.fq.gz	/mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion/data_chai/V350031121_L03_99_2.fq.gz

```
Import and visualisation commands
```
qiime tools import --type 'SampleData[PairedEndSequencesWithQuality]' --input-path ./manifest.tmp --output-path ./seq.qza --input-format PairedEndFastqManifestPhred33V2
qiime demux summarize --i-data seq.qza --o-visualization seq_summary.qzv
```
![image](https://github.com/AIKozyreva/Ivan-chai/assets/74992091/61103171-5d10-41a1-ad9f-dff44a87d33d)

Quality of data on the screen above. Based on plots decided to set some parameters like:
```
qiime dada2 denoise-paired [OPTIONS]
  --p-trunc-len-f INTEGER
                         Position at which forward read sequences should be
                         truncated due to decrease in quality. This truncates
                         the 3' end of the of the input sequences, which will
                         be the bases that were sequenced in the last cycles.
                         Reads that are shorter than this value will be
                         discarded. After this parameter is applied there must
                         still be at least a 12 nucleotide overlap between the
                         forward and reverse reads. If 0 is provided, no
                         truncation or length filtering will be performed
                                                                    [required]
  --p-trunc-len-r INTEGER
                         Position at which reverse read sequences should be
                         truncated due to decrease in quality. This truncates
                         the 3' end of the of the input sequences, which will
                         be the bases that were sequenced in the last cycles.
                         Reads that are shorter than this value will be
                         discarded. After this parameter is applied there must
                         still be at least a 12 nucleotide overlap between the
                         forward and reverse reads. If 0 is provided, no
                         truncation or length filtering will be performed
                                                                    [required]
  --p-trim-left-f INTEGER
                         Position at which forward read sequences should be
                         trimmed due to low quality. This trims the 5' end of
                         the input sequences, which will be the bases that
                         were sequenced in the first cycles.      [default: 0]
  --p-trim-left-r INTEGER
                         Position at which reverse read sequences should be
                         trimmed due to low quality. This trims the 5' end of
                         the input sequences, which will be the bases that
                         were sequenced in the first cycles.      [default: 0]
  --p-trunc-q INTEGER    Reads are truncated at the first instance of a
                         quality score less than or equal to this value. If
                         the resulting read is then shorter than `trunc-len-f`
                         or `trunc-len-r` (depending on the direction of the
                         read) it is discarded.                   [default: 2]
```
We have had primers:
> GGAAGGAGAAGTCGTAACAAGG 18S-ITS1F-new
> AGATATCCGTTGCCGAGAGT 58S-ITS1R-new
> ATCGAGTYTTTGAACGCAAGTTG 58S-ITS2F-new
> TCCTCCGCTTATTGATATGCT 28S-ITS2R-new

Command
```
qiime dada2 denoise-paired --i-demultiplexed-seqs demux-paired.qza --p-trunc-len-f 190 --p-trunc-len-r 165 --p-trunc-q 10 --p-trim-left-f 23 --p-trim-left-r 20 --o-table "./denoising/feature_table.qza" --o-representative-sequences "./denoising/rep_seqs.qza" --o-denoising-stats "./denoising/stats.qza" --verbose
```
