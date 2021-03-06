# Transfer Service sample using Java

This app creates two types of transfers using the Transfer Service tool.

## Prerequisites

1. Set up a project on Google Developers Console.
  1. Go to the [Developers Console](https://cloud.google.com/console) and create or select your project.
     You will need the project ID later.
1. Within Developers Console, select APIs & auth > Credentials.
  1. Select Add credentials > Service account > JSON key.
  1. Set the environment variable GOOGLE_APPLICATION_CREDENTIALS to point to your JSON key.
1. Add the Storage Transfer service account as an editor of your project
   storage-transfer-5031963314028297433@partnercontent.gserviceaccount.com
1. Set up gcloud for application default credentials.
  1. `gcloud components update`
  1. `gcloud auth login`
  1. `gcloud config set project PROJECT_ID`

## Transfer from Amazon S3 to Google Cloud Storage

Creating a one-time transfer from Amazon S3 to Google Cloud Storage.
1. Set up data sink.
  1. Go to the Developers Console and create a bucket under Cloud Storage > Storage Browser.
1. Set up data source.
  1. Go to AWS Management Console and create a bucket.
  1. Under Security Credentials, create an IAM User with access to the bucket.
  1. Create an Access Key for the user. Note the Access Key ID and Secret Access Key.
1. In AwsRequester.java, fill in the user-provided constants.
1. Run with `mvn compile` and
   `mvn exec:java -Dexec.mainClass="com.google.cloud.storage.storagetransfer.samples.AwsRequester"`
  1. Note the job ID in the returned Transfer Job.

## Transfer data from a standard Cloud Storage bucket to a Cloud Storage Nearline bucket

Creating a daily transfer from a standard Cloud Storage bucket to a Cloud Storage Nearline
bucket for files untouched for 30 days.
1. Set up data sink.
  1. Go to the Developers Console and create a bucket under Cloud Storage > Storage Browser.
  1. Select Nearline for Storage Class.
1. Set up data source.
  1. Go to the Developers Console and create a bucket under Cloud Storage > Storage Browser.
1. In NearlineRequester.java, fill in the user-provided constants.
1. Run with `mvn compile` and
   `mvn exec:java -Dexec.mainClass="com.google.cloud.storage.storagetransfer.samples.NearlineRequester"`
  1. Note the job ID in the returned Transfer Job.

## Checking the status of a transfer

1. In RequestChecker.java, fill in the user-provided constants. Use the Job Name you recorded earlier.
1. Run with `mvn compile` and
   `mvn exec:java -Dexec.mainClass="com.google.cloud.storage.storagetransfer.samples.RequestChecker"`
