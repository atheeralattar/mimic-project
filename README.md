# mimic-project
This project was part of the Big Data for Health Class CSE6250. It includes creating a local repo of the MIMIC database in order to facilitate the process for the reserachers to perform the data extraction and prediction tasks. Throughout the process we had several roadblocks especially with allocating the resources whether for the extraction step or for the model prediction step, these roadblock and any remidies are summerized below:

![image](https://user-images.githubusercontent.com/7920085/165003835-2351cb3f-20cc-4b2d-a489-0a1ea4de076c.png)

* Memory allocation needs, the whole projects needed ~67GB to store the data and another 50GB in RAM in order to be able to run the process.-
* The postgres server setup was also not straightforwad due to many library conflicts and especailly generating the concepts table.
* One of the main issues is that, the MIMIC_Extract project depends on generating and setting up the Postgres database and there is several conflict points when moving from the data tables generation repo to the MIMIC_Extract Repo. One of these issues is that the Postgres bash scripts generate the tables in two schemas, **mimiciii, public** while the MIMIC_Extract the script assumes that all the tables are in the **public** schema.
* In the MIMIC_Extract scripts, most of the issues were due to packages versioning confilcts. We have resolved all these conflicts by updating these versions, and for the benefit of any following research, we are sharing a snapshot of the environment libraries versions [requirements](https://github.com/atheeralattar/mimic-project/blob/main/requirements.txt) for the latest and greatest working version of the code.-
