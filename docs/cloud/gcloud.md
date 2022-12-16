# Google Cloud


## Authorization

1. Authorise access via browser using:

    ```bash
    $ gcloud auth login
    ```

2. To register gcloud for Docker so you can push to Google Container Registry:

    ```bash
    gcloud auth configure-docker
    ```

3. kubectl configuration for GKE

    ```bash
    gcloud container clusters get-credentials <CLUSTER_NAME> --zone <ZONE> --project <PROJECT_NAME>
    ```

## Replicate VSCode Environment







