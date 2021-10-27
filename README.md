# nhanes-pam-csv-data

NHANES physical activity monitoring data in CSV format, one file per one subject

## Data source

Centers for Disease Control and Prevention (CDC). National Center for Health Statistics (NCHS). National Health and Nutrition Examination Survey Data. Hyattsville, MD: U.S. Department of Health and Human Services, Centers for Disease Control and Prevention, 2003 - 2021, https://wwwn.cdc.gov/nchs/nhanes/.

Physical activity monitoring data only. The following table references NHANES studies that contained PAM monitoring data:


| Study code name | Years       | Source                                                                               | Number of subjects |
|-----------------|-------------|--------------------------------------------------------------------------------------|--------------------|
| C               | 2003 - 2004 | [NHANES](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2003) | 7176               |
| D               | 2005 - 2006 | [NHANES](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2005) | 7455               |
| G               | 2011 - 2012 | [NHANES](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2011) | 6917               |
| H               | 2013 - 2014 | [NHANES](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2013) | 7776               |

In total, 29324 participants.

## Data processing

Original data was downloaded from the NHANES web site in the `.xpt` or `.xpt.zip` formats. If compressed the data files were decompressed using [unzip](https://linux.die.net/man/1/unzip). Then `.xpt` files were converted into corresponding `.csv` files using [r-project](https://cran.r-project.org) and [foreign package](https://cran.r-project.org/web/packages/foreign/index.html). This resulted in one large `.csv` file per NHANES study. Finally, the large `.csv` files containing all records for a study was split into multiple `.csv` files using [nhanes-csv-split](https://github.com/o-mdr/pa-pattern-complexity/tree/main/src/nhanes-csv-split) application.

This process is easy to repeat by following instructions in the [pa-pattern-complexity](https://github.com/o-mdr/pa-pattern-complexity) repository.

For faster upload/download data was compressed using 

```bash
# sudo apt-get install p7zip-full

# -bt    show progress
# -mx7   default compression method, level 7 (out of 9)
# -v90m  split into chunks of ~90 MBs
# a      archive name
7z -bt -mx7 -v90m a data.7z data/

# git push --progress -v
# git pull
```

## Licence

This repository is licensed under the [Unlicense](LICENCE) and it is compatible with public domain.
[Original data](https://wwwn.cdc.gov/nchs/nhanes/NhanesCitation.aspx) is in the public domain.
