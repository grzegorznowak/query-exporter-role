# Query Exporter Role for Ansible

![Ansible Lint](https://github.com/grzegorznowak/query-exporter-role/actions/workflows/lint.yml/badge.svg)
![CI build](https://github.com/grzegorznowak/query-exporter-role/actions/workflows/ci.yml/badge.svg)
![CD build](https://github.com/grzegorznowak/query-exporter-role/actions/workflows/cd.yml/badge.svg)


Installs Query Exporter for Prometheus on Ubuntus as systemd

## Description

Deploys [query exporter](https://github.com/albertodonato/query-exporter).

Query Exporter has it's minimal requirement set to python 3.8. 
Which limits the array of distros it can be installed on easily. 
With the current release we're aiming for Unbuntus, to not over-complicate things initially. 
 
## Supported Distros

Adoption and support of more distributions will greatly depend on the users' feedback.

Please add your use cases to the issue tracker and we will triage those as we go.

### Ubuntu

* 20.04
* 18.04

## Installation

one of:
* `ansible-galaxy install grzegorznowak.query_exporter`
* clone the repo directly

## Usage

### Adjustable Defaults

For additional and low level configuration options head on to the `default.yml` file directly.
Those are the vars you might want to fiddle with normally: 
```
query_exporter_sources: https://github.com/albertodonato/query-exporter.git

# query_exporter_version: 2.7.0  unfortunatelly the last tag doesn't pass integration tests
# we use commit that we know is passing our test suite:
query_exporter_version: 1e97d1cfbf803f9f70747d248ce16ec58268849f

query_exporter_port: 9560
query_exporter_web_listen_address: "127.0.0.1"

# logging disabled by default, possible values are: CRITICAL, ERROR, WARNING, INFO, DEBUG
query_exporter_logging_level: false

# we use the original format of query exporter:
# https://github.com/albertodonato/query-exporter#configuration-file-format
# Additional inspiration can be found under in our tests' inventory file: 
# inventory/molecule/group_vars/all.yml:17

query_exporter_configuration:
  databases: []
  metrics: []
  queries: []
```

### Example with the role from Galaxy

```YAML
- name: Converge Query Exporters
  hosts: all
  
  roles:
    - grzegorznowak.query_exporter
```     

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
