---
layout: guide
title: Using mesheryctl
description: How to use mesheryctl
permalink: guides/mesheryctl
type: guide
---

### Meshery Lifecycle Management
Installation, troubleshooting and debugging of Meshery and its adapters.

| command   | flag      | function                  | Usage                     |
|:----------|:---------:|:--------------------------|:--------------------------|
|cleanup    |           | Pulls current meshery.yaml from meshery repo. *Warning: Any local changes will be overwritten.* | `mesheryctl cleanup` |
|log        |           | Starts tailing Meshery debug logs.                    | `mesheryctl log` |
|start      |           | Start all Meshery containers.                         | `mesheryctl start` |
|           | --reset   | (optional) reset Meshery's configuration file to default settings. | `mesheryctl start --reset` |
|status     |           | Displays the status of Meshery's containers.          | `mesheryctl status` |
|stop       |           | Stop all Meshery containers.                          | `mesheryctl stop` |
|           | --reset   | (optional) reset Meshery's configuration file to default settings. | `mesheryctl stop --reset` |
|update     |       |Pull new Meshery images from Docker Hub. Pulls new `mesheryctl` client. This command may be executed while Meshery is running. | `mesheryctl update` |
|version    |       |Displays the version of the Meshery Client (`mesheryctl`) and the SHA of the release binary.     | `mesheryctl version` |
|help       |       |Displays help about any command.     | `mesheryctl help` |

### Performance Management

| command   | flag                  | function                  | Usage                     |
|:----------|:---------------------:|:--------------------------|:--------------------------|
|perf       |                       | Performance Testing, Baselining and Benchmarking | `mesheryctl perf --name "a quick stress test" --url http://192.168.1.15/productpage --qps 300 --concurrent-requests 2 --duration 30s --load-generator wrk2` |
|           | --name                | (optional) A memorable name for the test. (default) a random string|  |
|           | --mesh optional)      | Name of the service mesh. (default) empty string | |
|           | --file (optional)     | URI to the service mesh performance test configuration file.<br>(default) empty string| `--file soak-test-clusterA.yaml` |
|           | --url (required)      | URL of the endpoint send load to during testing | `http://my-service/api/v1/test` |
|           | --qps (optional)      | Queries per second (default) 0| 0 - means to use the CPU unbounded to generate as many requests as possible.  |
|           | --concurrent-requests | (optional)| Number of concurrent requests<br>(default) 1 | `--concurrent-requests 10` |
|           | --duration (optional) | Duration of the test. | `10s`, `5m`, `2h` |
|           | --load-generator (optional)| choice of load generator: fortio (OR) wrk2 (default) fortio| `--load-generator=fortio`  |

### Service Mesh Lifecycle Management

| command    | arg          | flag          | function                             | Usage                     |
|:-----------|:-------------|:--------------|:-------------------------------------|:--------------------------|
| mesh       |              |               | Lifecycle management of service meshes|                          |
|            | init         |               | Provision a service mesh             |                           |
|            |              | profile       | Use specific configuration profile   | `--profile mTLS`          |
