### HCP_download : instructions specific to NeSI Mahuika cluster .i.e. slurm job arrarys,etc. 

 #### HCP S3 credentials
  To use this script, you need to create HCP credentials.  You'll need to accept the terms  of data usage as well.  You can do so by following (the beginning of) this tutorial:      https://wiki.humanconnectome.org/display/PublicData/How+To+Connect+to+Connectome+Data+    via+AWS).
   
    Once you have generated your credentials, create or append the following to `~/.aws/      credentials`:
    ```
     [hcp]
      AWS_ACCESS_KEY_ID=XXXXXXXXX
      AWS_SECRET_ACCES_KEY=XXXXXXXXXX
        ``````
    ```
 #### Setting up the Python environment

* Recommend using `Python/2.7.18-gimkl-2020` module for all of the processees
* Required Python Packages are *pandas*, *os*, *shutil* & *tarfile*. All but *pandas* comes with the python module. *pandas* can be installed via (or any other package which might be needed for future iterations) 

    ```bash 
    $ module load Python/2.7.18-gimkl-2020
    $ pip install --user pandas
            
    ```
 #### What are the datasets ?

* `subjects.txt` file contains all the subject IDs
* `download_HCP_1200.py` line 15-22 define the names of the databases
  * MEG_unprocessed
  * 3T_unprocessed
  * 7T_unprocessed
  * Diffusion
  * T1w
  * MNINonLinear
  * release-notes
  * MEG

#### Downloading datasets/dataset for a single subject

>**CAUTION** - These datasets can be quite large (~70GB per subject for all 8 datasets). Therefore, please do make sure to check the space of your nobabackup directory with `nn_storage_quota` command prior to starting the download

* Following command will download all of the datasets defined in line 15-22 `download_HCP_1200.py` for a single subject. In this instace, subject id is 996782

```bash
$ module load Python/2.7.18-gimkl-2020
$ python download_HCP_1200.py --subject=996782 --out_dir=/data/output/
```
* If the downloaded data to be used at a later date and required to be stored in comprresed format, use `--tartasks` flag

```bash
$ python download_HCP_1200.py --subeject=996782 --out_dir=/data/output/ --tartasks
```
* If you don't want to download all the datasets which is probably the case and recommended, comment out the ones which you want to exclude from `download_HCP_1200.py` prior to executing the command.For an example, if the databases of interst are `3T_unprocessed` & `7T_unprocessed`, then open `download_HCP_1200.py` file with a text editor and comment out the other 6 definitions with # .i.e. 

    ```python
    SERIES_MAP = {
    #'MEG_unprocessed':'unprocessed/MEG/',
    '3T_unprocessed':'unprocessed/3T/',
    '7T_unprocessed':'7T',
    #'Diffusion':'Diffusion',
    #'T1w':'T1w',
    #'MNINonLinear':'MNINonLinear',
    #'release-notes':'release-notes',
    #'MEG':'MEG'
    }
    ```
