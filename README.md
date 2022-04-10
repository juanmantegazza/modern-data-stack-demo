# airbyte - dbt - airflow - bigquery

1. Crate BigQuery dataset
```
airbyte_demo_dataset
```

2. Create Service Account, give BigQuery Roles and download keys
```bash
PROJECT_ID=$(gcloud config get-value project)
```
```bash
gcloud iam service-accounts create bigquery-sa --display-name="BigQuery SA"
```
```bash
gcloud projects add-iam-policy-binding ${PROJECT_ID} --member="serviceAccount:bigquery-sa@${PROJECT_ID}.iam.gserviceaccount.com" --role="roles/bigquery.user"
```
```bash
gcloud projects add-iam-policy-binding ${PROJECT_ID} --member="serviceAccount:bigquery-sa@${PROJECT_ID}.iam.gserviceaccount.com" --role="roles/bigquery.dataEditor"
```
```bash
gcloud iam service-accounts keys create bigquery-sa.json --iam-account=bigquery-sa@${PROJECT_ID}.iam.gserviceaccount.com
```

3. Set up Airbyte, Airflow and Superset with Docker Compose
```bash
./setup.sh up
```

4. Lauch Airbyte
```
http://localhost:8000
```

