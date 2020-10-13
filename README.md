# Time Series Analysis of Russian IRA Tweets

This repository contains a recipe for bootstrapping a project that does time series analysis on tweets from the [Internet Research Agency (IRA) open sourced by FiveThirtyEight](https://github.com/fivethirtyeight/russian-troll-tweets). The analysis in this project is bootstrapped using Apache Pinot and Superset.

## Usage

The example application in this repository bootstraps an Apache Pinot recipe for importing tweets by fake IRA Twitter accounts for analysis with Apache Superset.

To start the cluster, run the following commands.

```bash
$ docker network create PinotNetwork
$ docker-compose up -d
$ docker-compose logs -f --tail=100
```

After the Docker containers have started and are running, you'll need to bootstrap the cluster with the Twitter data and charts. The following command will download the raw CSV data from [this repository](https://github.com/kbastani/russian-troll-tweets) and start the Pinot ingestion job.

```bash
$ sh ./bootstrap.sh
```

After the bootstrap script has completed, you should be able to see data in Apache Pinot and be able to login to the Superset website. After logging into Superset, navigate to the dashboards to view the time series analysis of the IRA tweets.
