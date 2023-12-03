# Celanese Case: Cognite Data Fusion OPC-UA Extractor and Node-RED

Configuration files for Cognite Data Fusion, Node-RED and Telegraf (for debugging)
as a Docker Compose application stack

## Compose App

Bring the stack up:

```bash
docker compose --project-directory stack up -d
```

Bring stack down:

```bash
docker compose --project-directory stack down
```

Purge the stack:
```bash
docker compose --project-directory stack down --volumes
```

### Node-RED

NodeRED UI accessible at: `http://<ip-address>:1880`

Example simulation OPC-UA server flow in `nodered/flows.json`

Nodes Used:

- `node-red-contrib-iiot-opcua: 4.1.2`
- `node-red-nod-random: 0.4.1`

## External OPC-UA Clients

- [x] Tested on __ProSys OPCUA Browser / Simulation Server__
- [x] Tested on __Telegraf v1.27__ as OPC-UA Input Plugin



