
# Streaming ETL: optimize public transportation

## Project overview

Building streaming event pipeline around Apache Kafka and its ecosystem (REST Proxy, Kafka Connect). The result is a webpage that displays the status of train lines in real time.

## Project architecture

![Architecture for the project](/images/diagram.png)

## Running the project

### Pre-requisites

- Create a new virtual environment for the project (optional but highly recommended)
- Run 'requirements.txt' file to install dependencies for the project (pip install -r requirements.txt)

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

## Output

The output of the project looks like this
![Project output](/images/ui.png)