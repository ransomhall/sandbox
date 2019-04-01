# TICK Stack and node-red for TTN

This repo is a quick way to get the entire TICK Stack spun up and working together with [node-red](https://nodered.org/) and [The Things Network](https://thethingsnetwork.com) (TTN). It uses [Docker](https://www.docker.com/) to spin up the full TICK stack and node-red in a connected fashion. The [node-red docker](https://nodered.org/docs/platforms/docker) image (tagged latest) has been updated to include nodes for [InfluxDB](https://flows.nodered.org/node/node-red-contrib-influxdb) and [TTN](https://www.npmjs.com/package/node-red-contrib-ttn). This is heavily tested on MacOS and should mostly work on Linux and Windows. 

**Note: The Windows [batch file](/sandbox.bat) has not yet been updated to work out of the (sand)box as described below.**

To get started you need a running docker installation. If you don't have one, you can download Docker for [Mac](https://www.docker.com/docker-mac) or [Windows](https://www.docker.com/docker-windows), or follow the installation instructions for Docker CE for your [Linux distribution](https://docs.docker.com/engine/installation/#server).

### Running

To run the `sandbox`, simply use the convenient cli:

```bash
$ ./sandbox
sandbox commands:
  up           -> spin up the sandbox environment (add -nightly to grab the latest nightly builds of InfluxDB and Chronograf)
  down         -> tear down the sandbox environment
  restart      -> restart the sandbox
  influxdb     -> attach to the influx cli
  flux         -> attach to the flux REPL

  enter (influxdb||kapacitor||chronograf||telegraf) -> enter the specified container
  logs  (influxdb||kapacitor||chronograf||telegraf) -> stream logs for the specified container

  delete-data  -> delete all data created by the TICK Stack
  docker-clean -> stop and remove all running docker containers
  rebuild-docs -> rebuild the documentation container to see updates
```

To get started just run `./sandbox up`. You browser will open two tabs:

- `localhost:8888` - Chronograf's address. You will use this as a management UI for the full stack
- `localhost:3010` - Documentation server. This contains a simple markdown server for tutorials and documentation.

> NOTE: Make sure to stop any existing installations of `influxdb`, `kapacitor` or `chronograf`. If you have them running the Sandbox will run into port conflicts and fail to properly start. In this case stop the existing processes and run `./sandbox restart`. Also make sure you are **not** using _Docker Toolbox_.

Once the Sandbox launches, you should see your dashboard appear in your browser:

![Dashboard](./documentation/static/images/landing-page.png)

You are ready to get started with the TICK Stack!

Click the Host icon in the left navigation bar to see your host (named `telegraf-getting-started`) and its overall status.
![Host List](./documentation/static/images/host-list.png)

You can click on `system` hyperlink to see a pre-built dashboard visualizing the basic system stats for your
host, then check out the tutorials at `http://localhost:3010/tutorials`.

If you are using the nightly builds and want to get started with Flux, make sure you check out the [Getting Started with Flux](./documentation/static/tutorials/flux-getting-started.md) tutorial.

> Note: see [influx-stress](https://github.com/influxdata/influx-stress) to create data for your Sandbox.

![Dashboard](./documentation/static/images/sandbox-dashboard.png)

***

[what follows is a work in progress]

## Getting a device on The Things Network

TTN has excellent [documentation](https://www.thethingsnetwork.org/docs/devices/) for getting a LoRaWAN device communicating on the network.

### Getting started with node-red for TTN

Instructions for configuring node-red to work with TTN can be found [here](https://www.thethingsnetwork.org/docs/applications/nodered/quick-start.html#configure).


