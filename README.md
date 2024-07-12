# ai_on_edge_with_fiware
This is a project to implement an AI on Edge application with FIWARE. 

## Environment Setup
### Architecture
![Architecture](/docs/architecture.png)

### Prerequisites
- Docker
- Docker Compose
- Alternatively, Podman and Podman Compose

## Context Broker environment setup

[**Orion Context Broker**](https://fiware-orion.readthedocs.io/en/latest/) is used to manages context information.

[**MongoDB**](https://www.mongodb.com/) is used by the Orion Context Broker to hold context data information such as data entities, subscriptions and registrations.

To test if the Context Broker service is running correctly, send a GET request to the Context Broker's version endpoint, which should return version information if the service is up and running:

```bash 
curl http://localhost:1026/version
```
If the Context Broker is running correctly, you should receive a response similar to this:

```json
{
  "orionld version": "post-v1.5.1",
  "orion version":   "1.15.0-next",
  "uptime":          "0 d, 0 h, 15 m, 30 s",
  "git_hash":        "2c3d73c9ceafac5acbb726bd2c87d345998c7fa2",
  "compile_time":    "Wed Jun 5 22:23:13 UTC 2024",
  "compiled_by":     "root",
  "compiled_in":     "",
  "release_date":    "Wed Jun 5 22:23:13 UTC 2024",
  "doc":             "https://fiware-orion.readthedocs.org/en/master/"
}
```



