# Google Summer of Code - CHAOSS Microtasks
This Readme file provides the details of the microtasks that were successfully completed.

## Microtask 0:

Download and configure Augur, creating a dev environment using the general cautions noted here: https://oss-augur.readthedocs.io/en/dev/getting-started/installation.html and the full documentation here: https://oss-augur.readthedocs.io/en/dev/development-guide/toc.html

Status: Downloaded and configured augur with the database schema.
<img width="1440" alt="Microtask_0_install_success" src="https://user-images.githubusercontent.com/42388485/161753377-91880866-4369-4523-a37a-f76a5e057312.png">

------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="1432" alt="Microtask_0_augur" src="https://user-images.githubusercontent.com/42388485/161753507-d0bcda2f-c0b6-44d5-8564-dcc0491c7d96.png">

------------------------------------------------------------------------------------------------------------------------------------------------------


<img width="1428" alt="Microtask_0_augur_db" src="https://user-images.githubusercontent.com/42388485/161753562-22e8ef05-341e-408c-bbfb-cdfeed72ca09.png">



## Microtask 2:

Identify new issues you encounter during installation.

Status: 

Error 1: Encountered an error **SSL: CERTIFICATE_VERIFY_FAILED** while installing required NLTK word lists for machine learning workers.

Resolution:

I'm using Python 3.7 on Mac OSX and my mac doesn't have any local certificate to validate the SSL connections.
I found a file **Install Certificates.command** in **/Applications/Python 3.7** folder and running this file in a terminal installed the **certifi** python package which helps in validating the SSL connections. After installing the package, it then created a symbolic link from the OpenSSL certificates file to the certificates file installed by certifi. Using this helped in resolving the SSL error and successfully install the required workers.
<img width="1433" alt="Microtask_2_error_msg" src="https://user-images.githubusercontent.com/42388485/161753610-a75f7895-5cd8-4e92-bd89-b7c78ccc2d80.png">

------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="1412" alt="Microtask_2_resolution" src="https://user-images.githubusercontent.com/42388485/161753634-a19130fa-7bf2-4b42-bbe3-331d36dae894.png">

------------------------------------------------------------------------------------------------------------------------------------------------------

Error 2: Encountered database error **No Augur API key found.** while setting up augur and installing the database schema.
<img width="1361" alt="Microtask_2_db_error" src="https://user-images.githubusercontent.com/42388485/163698399-e685d095-4ee7-4a0d-9650-a0f8f668d31c.png">

------------------------------------------------------------------------------------------------------------------------------------------------------

Resolution:

After the error shows up, it found out an existing key in the database and prompted if the exisiting key needs to be replaced with the new one or not. Since, that was the first time I was setting up the schema, no previous key was generated. To find out if there's any existing api_key in the database, I connected to my created augur database and ran the query: **select * from "augur_operations"."augur_settings" where setting='augur_api_key';** and this query returned no rows. So, I went ahead and selected 'y' to replace the existing key and I encountered unique constraint error.
Summarizing the issue, no augur api key was found in the database yet it prompted the user that an api key already exists in the database.
Cleaning the build files and running make install helped in properly setting up the database schema.


## Microtask 4:

Anything you want to show us. Even if you find bugs in our documentation and want to issue a PR for those!

Status:

I found the links provided for pull_request_reports.py and contributor_reports.py and augur worker links as broken and raised a PR for the same:

https://github.com/chaoss/community/pull/340

https://github.com/chaoss/community/pull/342
