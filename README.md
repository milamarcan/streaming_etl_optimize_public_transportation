
# Streaming ETL: optimize public transportation

## Project overview

Building streaming event pipeline around Apache Kafka and its ecosystem (REST Proxy, Kafka Connect), that allows to simulate and display the status of train lines in real time. 

## Project assignment

You are constructing a streaming event pipeline around Apache Kafka and its ecosystem. Using public data from the [Chicago Transit Authority](https://www.transitchicago.com/data/) you will construct an event pipeline around Kafka that allows us to simulate and display the status of train lines in real time.
When the project is completed, you will be able to monitor a website to watch trains move from station to station.

## Project architecture

![Architecture for the project](/images/diagram.png)

## Running the project

### Pre-requisites

- Install [Docker](https://docs.docker.com/engine/install/), make sure Docker Compose is installed too
- If you are on Windows machine, install: Windows Subsystem for Linux (WSL) version 2 [link](https://learn.microsoft.com/en-us/windows/wsl/install)
- Install Ubuntu 20.04
- If you are on Windows machine, also install `librdkafka` library [link](https://github.com/confluentinc/librdkafka), make sure to install what is needed from [this link](https://docs.confluent.io/platform/current/installation/installing_cp/deb-ubuntu.html#get-the-software) too
- Inside Ubuntu, in a terminal instance run `docker-compose up`
    - You can check status of the environment by running `docker-compose ps` in a new terminal instance

### How to run the project

There are 2 pieces of the simulation, `producer` and `consumer`, each of them can be run separately. To run end-to-end simulation, run all the pieces together(in different terminal windows): 
1. To run the `producer`:
    - `cd producers`
    - `virtualenv venv`
    - `. venv/bin/activate`
    - `pip install -r requirements.txt`
    - `python simulation.py`
Hit `Ctrl+C` at any time to exit.

2. To run the Faust Stream Processing Application:
    - `cd consumers`
    - `virtualenv venv`
    - `. venv/bin/activate`
    - `pip install -r requirements.txt`
    - `faust -A faust_stream worker -l info`

3. To run the KSQL Creation Script:
    - `cd consumers`
    - `virtualenv venv`
    - `. venv/bin/activate`
    - `pip install -r requirements.txt`
    - `python ksql.py`

4. To run the `consumer`:
    - `cd consumers`
    - `virtualenv venv`
    - `. venv/bin/activate`
    - `pip install -r requirements.txt`
    - `cpython server.py`
Hit `Ctrl+C` at any time to exit.

### How to stop the project
- To stop Docker run `docker-compose stop` in a terminal instance
- To clean up the containers to reclaim disk space, run `docker-compose rm -v`

## Output

The output of the project looks like this
![Project output](/images/ui.png)