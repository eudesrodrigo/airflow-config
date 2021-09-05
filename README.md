# airflow-config
How to setup Airflow on Ubuntu

## Setup airflow environment variables
Airflow uses some environment variables to replace default config values on the airflow.cfg file.
The main environment variables are:

* AIRFLOW_HOME: Sets airflow's home directory where you can find the airflow.cfg, dags folder, etc.
** AIRFLOW_HOME="/root/airflow"

* AIRFLOW__CORE__SQL_ALCHEMY_CONN: Sets airflow's database connection string
** AIRFLOW__CORE__SQL_ALCHEMY_CONN="postgres://postgres:{password}@{host}:{port}/{db}"

You can use vim (command line text editor) to create/replace those environment variables:
```sh
sudo vi /etc/environment
```

## Install Airflow
### Install Ubuntu dependencies required for Apache Airflow.
```sh
sudo apt-get install libmysqlclient-dev ( for airflow airflow mysql )
```
```sh
sudo apt-get install libssl-dev ( for airflow cryptograph package)
```
```sh
sudo apt-get install libkrb5-dev (  for airflow kerbero package )
```
```sh
sudo apt-get install libsasl2-dev ( for airflow hive package )
```
```sh
After installing dependencies, Install Airflow and its packages.
```

### Airflow install
```sh
sudo pip install apache-airflow
```
for other subpackages like celery, async, crypto, rabbitmq etc., you can check apache airflow installation page

After successfully installing airflow, we will initialise Airflow’s database
```sh
airflow db init
```

Now airflow.cfg file should be generated in airflow home directory, we will tweak some configuration here to get better airflow functionality.

The basic airflow.cfg file is available to download here.

## Starting Airflow


## Stopping Aiflow
When you are running Airflow as a Daemon, it becomes little trickier to stop it. First you have to get process id of airflow and then kill it using sudo.

```sh
cat $AIRFLOW_HOME/airflow-webserver.pid
```
```sh
cat $AIRFLOW_HOME/airflow-scheduler.pid
```
above command will print Airflow process ID now kill it using command

```sh
sudo kill -9 {process_id of airflow}
```

## Aiflow errors
### Fail to access the Airflow Webpage
* Remove .pid files from $AIRFLOW_HOME directory and restart Ubuntu

# Useful commands
```sh
airflow next_execution <dag_id>
```