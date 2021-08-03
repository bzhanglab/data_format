# Composite continuous track (CCT) file

* File format description: a CCT file (`.cct`) is a data matrix in which each row represents a gene and each column represents a sample. 
   The first column lists the gene ids (e.g. gene symbols) and the first row lists the sample names. Two or more data
    columns are required. Columns must be separated by tab. Each cell in the matrix is a continuous value for 
    corresponding gene and sample. Missing values are represented by NA. Data for different samples must be comparable 
    (i.e. properly normalized). Duplicated row names or column names are not allowed. No special characters 
    for row or column names.
  
* Example:
  
| GeneSymbol | Sample1 | Sample2 | Sample3 | Sample4 |
|------------|---------|---------|---------|---------|
| Gene1      | 0.025   | -0.55   | -1      | 0.095   |
| Gene2      | -0.077  | 0.069   | 0.64    | 0.18    |
| Gene3      | -0.47   | 1       | 0.87    | -0.88   |
| Gene4      | -0.71   | -0.19   | 0.33    | -0.45   |


# Track sample information (TSI) file

* File format description: a TSI file (`.tsi`) is a data matrix in which each row represents a sample and each column
   represents one feature of the samples. Sample features can be divided into five data types: binary data 
   (BIN, e.g., mutation status), categorical data (CAT, e.g., tumor stage), continuous data (CON, e.g., age), 
   survival data (SUR, e.g. overall survival), and paired binary data (PAIRED, e.g. paired normal vs tumor).
    Binary data do not have to be 0/1 but must contain exactly two categories (e.g. yes/no or tumor/normal). 
    The first column lists the sample names. Sample names must match exactly those in the corresponding CCT. 
    The first row lists the feature names; and the second row indicates the data type for each feature (must be 
    one of the following: BIN, CAT, CON, SUR, or PAIRED). Each cell in the matrix is a value for corresponding 
    sample and feature. For survival data, time and event are separated by ",". For paired binary data, the pair
     id and binary value are separate by ",". Missing values are represented by NA. Duplicated row names or column names
    are not allowed. No special characters for row or column names are allowed.

* Example 

| Barcode         | Age | Anatomic neoplasm | Colonpolyps | Overall survival | Tissue   |
|-----------------|-----|-------------------|-------------|------------------|----------|
| data_type       | CON | CAT               | BIN         | SUR              | PAIRED   |
| TCGA-A6-2670-01 | 45  | sigmoid colon     | 0           | 259,0            | 1,batch1 |
| TCGA-A6-2671-01 | 85  | sigmoid colon     | 0           | 437,0            | 1,batch2 |
| TCGA-A6-2672-01 | 82  | transverse colon  | 0           | 1321,1           | 2,batch1 |
| TCGA-A6-2674-01 | 71  | sigmoid colon     | 0           | NA,NA            | 2,batch2 |
| TCGA-A6-2675-01 | 78  | sigmoid colon     | 0           | 434,0            | 3,batch1 |
| TCGA-A6-2676-01 | 75  | cecum             | 0           | 1437,1           | 3,batch2 |
| TCGA-A6-2677-01 | 68  | cecum             | 0           | 635,0            | 4,batch1 |
| TCGA-A6-2678-01 | 43  | transverse colon  | 0           | 437,0            | 4,batch2 |
| TCGA-A6-2679-01 | 73  | ascending colon   | 0           | 145,0            | 5,batch1 |
| TCGA-A6-2680-01 | 72  | hepatic flexure   | 0           | 465,1            | 5,batch2 |
| TCGA-A6-2681-01 | 73  | cecum             | 0           | 882,1            | 6,batch1 |
| TCGA-A6-2682-01 | 74  | cecum             | 0           | 889,1            | 6,batch2 |