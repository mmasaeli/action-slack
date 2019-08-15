# Action Slack

You can notify slack of GitHub Actions.

## Usage

### Succeeded Notification

![](https://user-images.githubusercontent.com/8043276/63113235-10a59a00-bfcd-11e9-83be-2dd8662c9ebb.png)

```yaml
- uses: 8398a7/action-slack@v1
  with:
    type: success
  env:
    SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

### Failed Notification

![](https://user-images.githubusercontent.com/8043276/63113244-14392100-bfcd-11e9-962b-03a19ba86680.png)

```yaml
- uses: 8398a7/action-slack@v1
  with:
    type: failed
  env:
    SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

### Custom Notification

![](https://user-images.githubusercontent.com/8043276/63113021-9f65e700-bfcc-11e9-97cf-9a962c7ce611.png)

```yaml
- uses: 8398a7/action-slack@v0
  with:
    payload: |
      {
        "text": "Custom Field Check",
        "attachments": [{
          "author_name": "slack-actions",
          "fallback": "fallback",
          "color": "good",
          "title": "CI Result",
          "text": "Succeeded",
          "fields": [{
            "title": "short title1",
            "value": "short value1",
            "short": true
          },
          {
            "title": "short title2",
            "value": "short value2",
            "short": true
          },
          {
            "title": "long title1",
            "value": "long value1",
            "short": false
          }],
          "actions": [{
          }]
        }]
      }
  env:
    SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

### Auto Notification

We are considering an automatic handling mode based on the job status.  
I'm leaving it because I don't seem to get the information.

```yaml
- uses: 8398a7/action-slack@v1
  with:
    type: auto
  env:
    SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```