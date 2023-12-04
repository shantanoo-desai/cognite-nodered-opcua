# Cognite Data Fusion OPC-UA Extractor and Node-RED

Configuration files for Cognite Data Fusion, Node-RED and Telegraf (for debugging)
as a Docker Compose application stack

## Scenario Reproduction

1. Clone Repo using `git clone https://github.com/shantanoo-desai/cognite-nodered-opcua.git`
2. Change into the directory `cd cognite-nodered-opcua`
3. Bring the stack up using:

    ```
     docker compose --project-directory stack up -d
    ```
4. Head to `http://<ip-address>:4840` or `http://localhost:4840` in a browser to go to Node-RED editor
5. Install the required nodes mentioned below using the __Palette Manager__ from the Node-RED editor
6. Import the example flow from the __Import__ menu in Node-RED and upload the flow file in the `nodered` directory of this repo
7. Deploy the flow using the __Deploy__ button
8. Observe Logs:

    ```
     docker compose --project-directory stack logs -f cognite
    ```
9. Reboot the Linux machine `sudo reboot`
10. Wait for the containers to boot post system reboot and check cognite logs again (step 8)


## Compose App

Docker Engine Version:  24.0.7
Docker Compose Version: 2.21.0

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

## Node-RED

NodeRED UI accessible at: `http://<ip-address>:1880`

### Nodes
Install the following nodes from the Node-RED Editor via the Palette Manager:

- `node-red-contrib-iiot-opcua: 4.1.2`
- `node-red-node-random: 0.4.1`

### Flow

Copy the flow in the `nodered/flows.json` file and import it in Node-RED via the Editor.

Once imported click on the __Deploy__ button in the Node-RED editor to generate random values
from an OPC-UA Server.

The OPC UA Server will be available on:

- `http://ip-address-machine:4840` for external OPC-UA Clients
- `http://cognite-nodered:4840` for containers on the same docker network


## Cognite OPC-UA Extractor

Current Version: 2.22.1

### Add CDF Credentials

Create a `.env` file in the `cognite` directory and add the following environment variables in the file:

```
CDF_DEV_ID=<YOUR_DEV_ID_HERE>
CDF_DEV_PROJECT=<DEV_PROJECT_HERE>
CDF_DEV_SECRET=<DEV_SECRET_HERE>
CDF_TENANT=<TENANT_HERE>
```

### Logs

Logs from the container are stored in the `cognite/logs` directory on the host

## Telegraf

Telegraf Version: 1.27.2-alpine


## External OPC-UA Clients

- [x] Tested on __ProSys OPCUA Browser / Simulation Server__
- [x] Tested on __UAExpert v1.6.2 438__

## Logs

### Node-RED Logs

```bash
docker compose --project-directory stack logs -f nodered
```

### Cognite Logs

```bash
docker compose --project-directory stack logs -f cognite
```

### Telegraf Logs

```bash
docker compose --project-directory stack logs -f telegraf
```



