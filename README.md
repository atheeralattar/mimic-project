# Physionet Data Extraction MIMIC_III Project
This project was part of the Big Data for Health Class CSE6250. It includes creating a local repo of the MIMIC database in order to facilitate the process for the reserachers to perform the data extraction and prediction tasks. Throughout the process we had several roadblocks especially with allocating the resources whether for the extraction step or for the model prediction step, these roadblock and any remidies are summerized below:

![image](https://user-images.githubusercontent.com/7920085/165003835-2351cb3f-20cc-4b2d-a489-0a1ea4de076c.png)

* Memory allocation needs, the whole projects needed ~67GB to store the data and another 50GB in RAM in order to be able to run the process.-
* The postgres server setup was also not straightforwad due to many library conflicts and especailly generating the concepts table.
* One of the main issues is that, the MIMIC_Extract project depends on generating and setting up the Postgres database and there is several conflict points when moving from the data tables generation repo to the MIMIC_Extract Repo. One of these issues is that the Postgres bash scripts generate the tables in two schemas, **mimiciii, public** while the MIMIC_Extract the script assumes that all the tables are in the **public** schema.
* In the MIMIC_Extract scripts, most of the issues were due to packages versioning confilcts. We have resolved all these conflicts by updating these versions, and for the benefit of any following research, we are sharing a snapshot of the environment libraries versions [requirements](https://github.com/atheeralattar/mimic-project/blob/main/requirements.txt) for the latest and greatest working version of the code.
* We also changed some of the functions and corrected some sytanxes in the main extract code, in addition to updating some deprecated commands (e.g. df.idx) and also the library imports were either updated or replaced with a [working version](https://github.com/atheeralattar/mimic-project/blob/main/mimic_direct_extract.py) to eliminate the errors due to versioning. The final version of the extract code was also shared in this repo.
* The Postgres script that generates the concepts tables and views in the two schemas (public and mimiciii) also experienced some errors due to the use of REGEX pattern to strip the dates, we needed to modify the pattern as this a well known issue addresed in the issues of the [MIT-LCP](https://github.com/MIT-LCP/) repo which is an essential step needs to be completed before running the [MIMIC_Extract](https://github.com/MLforHealth/MIMIC_Extract) repo.
* Due to the nature the concepts tables are generated, they are placed under different schema **public** while the MIMIC_Extract script expects these tables to be under **mimiciii** schema, to solve this issue the following command needs to be ran for each table under PUBLIC schema ```ALTER TABLE code_status SET SCHEMA mimiciii``

