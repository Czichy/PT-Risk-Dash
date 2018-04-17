![Screenshot 1](https://github.com/mehtadone/PT-Risk-Dash/blob/master/dash.png?raw=true)

## What is this?
This is a dashboard I built for personal use that utilises Grafana, postgresql and a script to take statistics from the Profit Trailer json file to a database so that I can view metrics that are important to me. It is not ideal as it does not take information from the exchange but will work as an approximation for now. 

## Why did you do this?
Having spent 15 years developing software for Forex trading desks, the most important tool in their arsenal is a risk management tool. Any proprietary trading desk or a flow desk, needs to see their risk exposure, not just the big fat profit figure. This is something that was missing for me, and hence I put this together. 

## Who is this for?
This is not a simple one click install application. It requires a bit of installation and expertise to put together. There are far better and easier tools out there if you want profit figures only. This is for someone who wants to manage their risk, and also over multiple bots.

## How much is it?
Nothing. It is fully open source, like [CryptoGramBot](https://github.com/mehtadone/CryptoGramBot). 

## How do I install it? Option 1 (To be improved)

1. Install Grafana beta 5
2. Install postgresdb, if not already installed
3. Run sql scripts on new postgres db
(db is called pt_binance. Probably should be renamed)
4. Run js file on a cron job with parameters
(host,port,password, schema_name)
There maybe some dependencies you'll to install for node. If you run the js file manually, you'll see them. There are 2 or 3
5. Import the json dashboards into grafana. (Trex, Binance BTC, Binance ETH and PT Combined BTC added as an example)

## How do I install it? option 2 (To be improved)
1. Install docker
2. Install docker-compose
2. Install nodejs
```
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt install -y nodejs
```
3. Installation grafana 5, postgres and pgadmin via docker
```
docker-compose up -d
```
4. Install nodejs package and run script
```
cd pt-exporter
npm install
node ptlogger.js 127.0.0.1 8081 pt_password binance
```

## Issues

1. If Grafana does not find the given source directly, you have to delete the data source and recreate it manually (I suspect a bug in grafana v5 with the option "sslmode: disable" in the datasource.yml file)

2. If you want to display the values in USD/EUR and not GBP by default, you will have to modify the references in the graphs.


## Huge thanks

- Inspiration from [GeekLingo](https://github.com/geeklingo/Guppy-Dashboard)
- YoJeff for his initial grafana script
- The PT Crew
