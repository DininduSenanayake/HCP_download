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
