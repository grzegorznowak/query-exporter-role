# Query Exporter Role

![Ansible Lint](https://github.com/grzegorznowak/query-exporter-role/actions/workflows/lint.yml/badge.svg)
![CI Sources Integration](https://github.com/grzegorznowak/query-exporter-role/actions/workflows/ci.yml/badge.svg)
![CI Binary Integration](https://github.com/grzegorznowak/query-exporter-rolee/actions/workflows/cd.yml/badge.svg)


Installs Query Exporter for Prometheus on Ubuntus as systemd service with Ansible

## Description

Deploys [query exporter](https://github.com/albertodonato/query-exporter).

Query Exporter has it's minimal requirement set to python 3.8. 
Which limits the array of distroy it can be installed easily. 
With the current release we're aiming for Unbuntus, to not over-complicate things initially. 
 
## Supported Distros

Adoption and support of more distributions will greatly depend on the users' feedback.

Please add your use cases to the issue tracker and we will triage those as we go.

### Ubuntu

* 20.04
* 18.04

## Integration Testing


### CI pipeline

CI ran against LXD on github runners for each meaningful commit and merge to the main branch 

### locally on LXD

LXD should already be installed and configured.

Trigger the full suite with `./test-local.sh`

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)


## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
