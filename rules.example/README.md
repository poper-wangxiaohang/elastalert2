# ElastAlert Rules

```
$ mkdir rules/
$ cp rules.example/*.yaml.example rules/
$ cd rules/
$ cp ***.yaml.example ***.yaml

$ vi ***.yaml
# And then, edit the following vars:
es_host: ***
es_port: ***
es_username: ***
es_password: ***
timeframe: ***
filter: ***
index: basic_log-*
alert_subject: "<@slack-user-id>alert-subject"
slack_webhook_url: 'https://hooks.slack.com/services/***'
slack_channel_override: "#slack-channel-name"
slack_title: "<@slack-user-id>slack-title"
kibana_discover_app_url: "http://kibana.url/app/discover#/"
kibana_discover_index_pattern_id: "kibana-index-id"
kibana_discover_version: "7.16"
```
