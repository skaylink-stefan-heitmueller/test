# demo jobapi

## setup token

* goto https://github.com/settings/apps
* add new fine-grained personal access token
  * grant read and write access to actions

## start

### payload

```json
{
  "ref": "main",
  "inputs": {
    "uuid": "6d7e46b9-5099-4aa9-8cdf-28e39d826c55",
    "callback": "https://foo.bar",
    "environment": "foo-bar-stage-eu-central-1",
    "instance_id": "i-1337"
  }
}
```

### start

```bash
curl -f -d@payload -H "accept: application/vnd.github+json" -H "authorization: token ${token}" https://api.github.com/repos/skaylink-stefan-heitmueller/test/actions/workflows/aws-ec2-restart.yml/dispatches
```

### get

```bash
curl -sf -H "accept: application/vnd.github+json" -H "authorization: token ${token}" "https://api.github.com/repos/skaylink-stefan-heitmueller/test/actions/runs?event=workflow_dispatch&created>2024-05-08T09:00:00" | jq '.workflow_runs[] | select(.display_title=="aws-ec2-restart-6d7e46b9-5099-4aa9-8cdf-28e39d826c55")'
```
