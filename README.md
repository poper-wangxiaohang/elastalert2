# ElastAlert 2

ElastAlert 2 is a standalone software tool for alerting on anomalies, spikes, or other patterns of interest from data in [Elasticsearch][10] and [OpenSearch][9].

ElastAlert 2 is backwards compatible with the original [ElastAlert][0] rules.

![CI Workflow](https://github.com/jertel/elastalert/workflows/master_build_test/badge.svg)

## Deployment

```
# 1. ElastAlert .env
$ cp .env.example .env
# Edit Env Config Vars ...

# 2. ElastAlert Configuration
$ cp elastalert.yaml.example elastalert.yaml
# OR:
$ cp elastalert.yaml.simple elastalert.yaml
# And then, edit the following vars:
es_host: ***
es_port: ***
es_username: ***
es_password: ***
run_every: ***
buffer_time: ***

# 3. ElastAlert Rules
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

# 4. Debug: Test Your ElastAlert Rules
$ docker-compose exec elastalert bash
# debug tool:
$ elastalert-test-rule --help
$ elastalert-test-rule rules/some-elastalert-rule.yaml
$ elastalert-test-rule rules/some-elastalert-rule.yaml --alert
```

## Docker and Kubernetes

ElastAlert 2 is well-suited to being run as a microservice, and is available
as an image on [Docker Hub][2] and on [GitHub Container Registry][11]. For more instructions on how to
configure and run ElastAlert 2 using Docker, see [here][8].

A [Helm chart][7] is also included for easy configuration as a Kubernetes deployment. 

## Documentation

Documentation, including an FAQ, for ElastAlert 2 can be found on [readthedocs.com][3]. This is the place to start if you're not familiar with ElastAlert 2 at all.

Elasticsearch 8 support is documented in the [FAQ][12].

The full list of platforms that ElastAlert 2 can fire alerts into can be found [in the documentation][4].

## Contributing

Please see our [contributing guidelines][6].

## License

ElastAlert 2 is licensed under the [Apache License, Version 2.0][5].

[0]: https://github.com/yelp/elastalert
[1]: https://github.com/jertel/elastalert2/blob/master/examples/config.yaml.example
[2]: https://hub.docker.com/r/jertel/elastalert2
[3]: https://elastalert2.readthedocs.io/
[4]: https://elastalert2.readthedocs.io/en/latest/ruletypes.html#alerts
[5]: https://www.apache.org/licenses/LICENSE-2.0
[6]: https://github.com/jertel/elastalert2/blob/master/CONTRIBUTING.md
[7]: https://github.com/jertel/elastalert2/tree/master/chart/elastalert2
[8]: https://elastalert2.readthedocs.io/en/latest/running_elastalert.html
[9]: https://opensearch.org/
[10]: https://github.com/elastic/elasticsearch
[11]: https://github.com/jertel/elastalert2/pkgs/container/elastalert2%2Felastalert2
[12]: https://elastalert2.readthedocs.io/en/latest/recipes/faq.html#does-elastalert-2-support-elasticsearch-8
