# GitHub Action for Google Cloud

The GitHub Actions for [Google Cloud Platform](https://cloud.google.com/) and wraps the [gcloud SDK](https://cloud.google.com/storage/docs/gsutil_install) to enable common Google Cloud Util commands. This is a thin wrapper around the `gsutil` utility.

## Usage

An example workflow to list clusters on Google Cloud Platform:

```
workflow "Run gcloud command" {
  on = "push"
  resolves = "Load credentials"
}

action "GCP Authenticate" {
  uses = "actions/gcloud/auth@master"
  secrets = ["GCLOUD_AUTH"]
}

action "GCP List Clusters" {
  needs = ["GCP Authenticate"]
  uses = "actions/gcloud/gsutil@master"
  args = "cp [PATH_TO_FILE_OR_DIRECTORY] gs://[STORAGE_ID]
}
```

For more information about the authentication step, [see `auth`](/auth).

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT License](LICENSE).

Container images built with this project include third party materials. See [THIRD_PARTY_NOTICE.md](THIRD_PARTY_NOTICE.md) for details.
