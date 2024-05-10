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
Import command
```
qiime tools import --type 'SampleData[PairedEndSequencesWithQuality]' --input-path ./manifest.tmp --output-path ./seq.qza --input-format PairedEndFastqManifestPhred33V2
```
