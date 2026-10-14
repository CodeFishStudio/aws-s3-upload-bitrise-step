# Amazon Web Services (AWS) S3 Upload

[![Step changelog](https://shields.io/github/v/release/bitrise-steplib/bitrise-step-aws-s3-upload?include_prereleases&label=changelog&color=blueviolet)](https://github.com/bitrise-steplib/bitrise-step-aws-s3-upload/releases)

> **CodeFish Studio fork** of [bitrise-steplib/bitrise-step-aws-s3-upload](https://github.com/bitrise-steplib/bitrise-step-aws-s3-upload).
> Fixes [upstream issue #5](https://github.com/bitrise-steplib/bitrise-step-aws-s3-upload/issues/5): the `acl_control` input was never sent to S3, so `public-read` uploads stayed private.
>
> Use it in `bitrise.yml`:
>
> ```yaml
> - git::https://github.com/CodeFishStudio/aws-s3-upload-bitrise-step.git@main:
>     inputs:
>     - path: $BITRISE_IPA_PATH
>     - bucket_name: my-bucket
>     - bucket_prefix: client-builds/$BITRISE_BUILD_NUMBER
>     - acl_control: public-read
> ```
>
> `public-read` requires the bucket to have ACLs enabled (Object Ownership: "ACLs enabled") and the ACL settings under Block Public Access turned off.

The Step uploads a file to an Amazon S3 bucket.

<details>
<summary>Description</summary>

The Step uploads a file to an Amazon S3 bucket.

It can handle both files and directories, uploading the contents to the specified S3 bucket with the desired access control settings.

Using the Authenticate with AWS Step beforehand is recommended to securely provide short lived AWS credentials.
</details>

## 🧩 Get started

Add this step directly to your workflow in the [Bitrise Workflow Editor](https://docs.bitrise.io/en/bitrise-ci/workflows-and-pipelines/steps/adding-steps-to-a-workflow.html).

You can also run this step directly with [Bitrise CLI](https://github.com/bitrise-io/bitrise).

## ⚙️ Configuration

<details>
<summary>Inputs</summary>

| Key | Description | Flags | Default |
| --- | --- | --- | --- |
| `path` | Path to a file or folder to be uploaded.  You can use absolute or relative paths. | required |  |
| `bucket_name` | Name of the S3 bucket to upload the file to. | required |  |
| `bucket_prefix` | Path in the S3 bucket where the file will be uploaded.  If not provided, the file will be uploaded to the root of the bucket with its original filename. |  |  |
| `acl_control` | The access control level for the uploaded file. | required | `private` |
| `region` | The AWS region to use. | required | `us-east-1` |
| `access_key_id` | The AWS Access Key ID.  You can provide it directly or use the Authenticate with AWS Step. | required | `$AWS_ACCESS_KEY_ID` |
| `secret_access_key` | The AWS Secret Access Key.  You can provide it directly or use the Authenticate with AWS Step. | required | `$AWS_SECRET_ACCESS_KEY` |
| `session_token` | The AWS Session Token.  You can provide it directly or use the Authenticate with AWS Step. |  | `$AWS_SESSION_TOKEN` |
| `verbose` | Enable logging additional information for debugging. | required | `false` |
</details>

<details>
<summary>Outputs</summary>
There are no outputs defined in this step
</details>

## 🙋 Contributing

We welcome [pull requests](https://github.com/bitrise-steplib/bitrise-step-aws-s3-upload/pulls) and [issues](https://github.com/bitrise-steplib/bitrise-step-aws-s3-upload/issues) against this repository.

For pull requests, work on your changes in a forked repository and use the Bitrise CLI to [run step tests locally](https://docs.bitrise.io/en/bitrise-ci/bitrise-cli/running-your-first-local-build-with-the-cli.html).

Learn more about developing steps:

- [Create your own step](https://docs.bitrise.io/en/bitrise-ci/workflows-and-pipelines/developing-your-own-bitrise-step/developing-a-new-step.html)
