# Loading Data into Cloud SQL || [GSP196](https://www.cloudskillsboost.google/focuses/1157?parent=catalog) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell

```
export REGION=
```
```
gcloud auth list

git clone \
   https://github.com/GoogleCloudPlatform/data-science-on-gcp/

cd data-science-on-gcp/03_sqlstudio

export PROJECT_ID=$(gcloud info --format='value(config.project)')
export BUCKET=${PROJECT_ID}-ml

gsutil cp create_table.sql \
    gs://$BUCKET/create_table.sql

gcloud sql instances create flights \
    --database-version=POSTGRES_13 --cpu=2 --memory=8GiB \
    --region=$REGION --root-password=Passw0rd

export ADDRESS=$(curl -s http://ipecho.net/plain)/32

gcloud sql instances patch flights --authorized-networks $ADDRESS --quiet

export INSTANCE_NAME=flights
export DATABASE_NAME=bts
export SQL_FILE=create_table.sql

# Create a database
gcloud sql databases create $DATABASE_NAME --instance=$INSTANCE_NAME

SERVICE_ACCOUNT_EMAIL=$(gcloud sql instances describe $INSTANCE_NAME --format='value(serviceAccountEmailAddress)')

gsutil iam ch serviceAccount:$SERVICE_ACCOUNT_EMAIL:roles/storage.objectViewer gs://$BUCKET

# Import the SQL file into the database
gcloud sql import sql $INSTANCE_NAME \
    gs://$BUCKET/$SQL_FILE \
    --database=$DATABASE_NAME \
    --quiet
```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
