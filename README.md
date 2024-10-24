# bq-datasets-tables-module-terraform


TODO : write description for project


## Build from local machine

### Set env vars in your Shell

```shell
export PROJECT_ID="burner-mankumar24-02"
export LOCATION="us-central1"
export TF_STATE_BUCKET="mk-ps-us-central1-stb-01"
export TF_STATE_PREFIX="bq-resources"
export WORKSPACE="workspacetest"
export INFRA_ROOT_FOLDER="infra"
export MODULE_NAME="datasets_and_tables"
export GOOGLE_PROVIDER_VERSION="= 4.47.0"
```

### Plan with workspace

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-plan-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

### Plan without workspace

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-plan-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

### Apply with workspace

```shell
    gcloud builds submit \
        --project=$PROJECT_ID \
        --region=$LOCATION \
        --config terraform-apply-modules.yaml \
        --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
        --verbosity="debug" .
```


test


### Apply without workspace

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-apply-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

### Destroy with workspace

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-destroy-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

### Destroy without workspace

```shell
gcloud builds submit \
    --project=$PROJECT_ID \
    --region=$LOCATION \
    --config terraform-destroy-modules.yaml \
    --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=,_INFRA_ROOT_FOLDER=$INFRA_ROOT_FOLDER,_MODULE_NAME=$MODULE_NAME,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
    --verbosity="debug" .
```

## Build from the project hosted in a GITHUB repository

### Plan

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="bq-datasets-tables-module-terraform-plan" \
  --repo="https://github.com/mr-manoj-dev/bq-datasets-tables-module-terraform" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="terraform-plan-modules.yaml" \
  --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
  --verbosity="debug"
```

### Apply

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="bq-datasets-tables-module-terraform-apply" \
  --repo="https://github.com/mr-manoj-dev/bq-datasets-tables-module-terraform" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="terraform-apply-modules.yaml" \
  --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
  --verbosity="debug"
```

### Destroy

```shell
gcloud beta builds triggers create manual \
  --project=$PROJECT_ID \
  --region=$LOCATION \
  --name="bq-datasets-tables-module-terraform-destroy" \
  --repo="https://github.com/mr-manoj-dev/bq-datasets-tables-module-terraform" \
  --repo-type="GITHUB" \
  --branch="main" \
  --build-config="terraform-destroy-modules.yaml" \
  --substitutions _TF_STATE_BUCKET=$TF_STATE_BUCKET,_TF_STATE_PREFIX=$TF_STATE_PREFIX,_WORKSPACE=$WORKSPACE,_GOOGLE_PROVIDER_VERSION=$GOOGLE_PROVIDER_VERSION \
  --verbosity="debug"
```


