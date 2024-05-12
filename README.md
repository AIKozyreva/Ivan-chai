# Ivan-chai
ivan-chai data by QIIME2 for Ivan

Raw data: /mnt/SSD4TB/STORAGE/240412_MGI_ITS

my Project folder: /mnt/SSD4TB/PROJECTS/kozyreva_works/qiime2/chamaenerion 

## QIIME2 + DADA2 + pretrained NaiveBayes + Unite ver 9.0 db (UNiref97-99 for all euk version for 2023.2)

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
**Import and visualisation commands**

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
**We have had primers:**
> GGAAGGAGAAGTCGTAACAAGG 18S-ITS1F-new
> AGATATCCGTTGCCGAGAGT 58S-ITS1R-new

> ATCGAGTYTTTGAACGCAAGTTG 58S-ITS2F-new
> TCCTCCGCTTATTGATATGCT 28S-ITS2R-new

_______________________________________________________________________________________________________________________________________________
### Denoising DADA2 Command
```
qiime dada2 denoise-paired --i-demultiplexed-seqs demux-paired.qza --p-trunc-len-f 190 --p-trunc-len-r 165 --p-trunc-q 10 --p-trim-left-f 23 --p-trim-left-r 20 --o-table "./denoising/feature_table.qza" --o-representative-sequences "./denoising/rep_seqs.qza" --o-denoising-stats "./denoising/stats.qza" --verbose
```
_________________________________________________________________________________________________________________________________________________
### Classifier
Сначала попробуем использовать классификатор натренированный на старой (2023 года) версии БД unite: https://github.com/colinbrislawn/unite-train/releases/tag/9.0-qiime2-2023.2-demo . 
```
mkdir taxonomy
qiime feature-classifier classify-sklearn --i-classifier ../unite_ver9_dynamic_all_29.11.2022-Q2-2023.2.qza --i-reads denoising/rep_seqs.qza --o-classification "taxonomy/taxonomy.qza" --p-confidence 0.94
qiime tools export --input-path "taxonomy/taxonomy.qza" --output-path "taxonomy"
qiime tools export --input-path "denoising/feature_table.qza" --output-path "denoising/"
biom convert -i "denoising/feature-table.biom" -o "denoising/feature-table.tsv" --to-tsv
```
Так, это у нас таблица почищенных features (в таблице лист feature-table), где каждая строка цифро-букв - это уникальный набор "одинаково похожих" последовательностей. На следующем шаге collapse мы объединяем все features, у которых одна и та же таксономия. 

```
qiime taxa collapse --i-table "denoising/feature_table.qza" --i-taxonomy "taxonomy/taxonomy.qza" --p-level 6 --o-collapsed-table "collapsed_feature_table.qza"
qiime tools export --input-path "./collapsed_feature_table.qza" --output-path "./"
biom convert -i "./feature-table.biom" -o "./collapsed_feature_table.tsv" --to-tsv
```
Таблица сохранена и находится на листе "collapsed_feature_table". Далее пробуем построить heatmap для наглядности.
```
qiime feature-table heatmap --i-table ./collapsed_feature_table.qza --p-no-normalize --p-color-scheme Purples_r --o-visualization ./collapsed_feature_table_heatmap #картинка 1 наглядно ясно, что при таких больших разбросах делать без нормализции - это плохая идея...
qiime feature-table heatmap --i-table ./collapsed_feature_table.qza --p-color-scheme Purples_r --o-visualization ./norm_collapsed_feature_table_heatmap #картинка 2 ситуация the same, но график поприятнее
```
![image](https://github.com/AIKozyreva/Ivan-chai/assets/74992091/d862f385-9d37-4682-ba2b-d91847244c80)

![image](https://github.com/AIKozyreva/Ivan-chai/assets/74992091/eb291552-14d8-4d86-813b-c94f5582ee85)

Кажется, "для наглядности" лучше смотреть в таблицу.

_______________________________________________________________________________________________________________________________________________
### Relative-frequency
В общем ещё есть вариант посчитать не общее распределение, а относительное. Это вот такое:
>This relative-freq table only providing me number of seq per sample and the occurrence of each feature in the whole sample.
>We’d like to see, for example, that proteobacteria proportionally makes up 55% (0.55) of sample 1, but 75% (0.75) of sample 2. 
```
qiime feature-table relative-frequency --i-table collapsed_feature_table.qza --o-relative-frequency-table ./relative/rel-phyla-table.qza
qiime tools export --input-path "./relative/rel-phyla-table.qza" --output-path "./relative/"
biom convert -i "./relative/feature-table.biom" -o "./relative/rel_collapsed_feature_table.tsv" --to-tsv
```
Все таблички на листах с соответствующими названиеми в файле res_table_uniteDB_ph6_2023.xlsx



## QIIME2 + DADA2 + pretrained NaiveBayes + Unite ver 10.0 db (unite_ver10_97_all_04.04.2024-Q2-2024.2.qza)

### Import and Denoising DADA2 Commands are the same
### Classifier
Попробуем использовать классификатор натренированный на новой (2024 года) версии БД unite: https://github.com/colinbrislawn/unite-train/releases/tag/v10.0-v04.04.2024-qiime2-2024.2 Всё,  конечно, хорошо, но для этого придётся обновить QIIMe2 до версии 2024ю2, а то он иначе не хочет (удивительно да)
```
mkdir taxonomy
qiime feature-classifier classify-sklearn --i-classifier ../unite_ver10_97_all_04.04.2024-Q2-2024.2.qza --i-reads denoising/rep_seqs.qza --o-classification "taxonomy/taxonomy.qza" --p-confidence 0.94
qiime tools export --input-path "taxonomy/taxonomy.qza" --output-path "taxonomy"
qiime tools export --input-path "denoising/feature_table.qza" --output-path "denoising/"
biom convert -i "denoising/feature-table.biom" -o "denoising/feature-table.tsv" --to-tsv
```
Далее все команды аналогичные прошлому подходу.
```
qiime taxa collapse --i-table "denoising/feature_table.qza" --i-taxonomy "taxonomy/taxonomy.qza" --p-level 7 --o-collapsed-table "collapsed7_feature_table.qza"
qiime tools export --input-path "./collapsed7_feature_table.qza" --output-path "./"
biom convert -i "./feature-table.biom" -o "./collapsed7_feature_table.tsv" --to-tsv
qiime feature-table heatmap --i-table ./collapsed7_feature_table.qza --p-color-scheme Purples_r --o-visualization ./norm_collapsed7_feature_table_heatmap
```
![image](https://github.com/AIKozyreva/Ivan-chai/assets/74992091/9c90a041-ad68-4a57-9ff1-e2b690fe4416)
_______________________________________________________________________________________________________________________________________________
### Relative-frequency
```
qiime feature-table relative-frequency --i-table collapsed7_feature_table.qza --o-relative-frequency-table ./relative/rel-phyla7-table.qza
qiime tools export --input-path "./relative/rel-phyla7-table.qza" --output-path "./relative/"
biom convert -i "./relative/feature-table.biom" -o "./relative/rel_collapsed7_feature_table.tsv" --to-tsv
```

Все данныые на листах внутри таблицы res_table_unite10DB_ph7_2024.xl и в папке with_unite-10
