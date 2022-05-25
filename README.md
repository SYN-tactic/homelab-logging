This contains logic needed for running a logging system on my local 
network.

Steps for making sure this works:
- Open up the needed ports. Make sure they only accept connections from the local network.
- Make sure your .env file is setup with a password for Graylog.
- run `docker-compose up -d`
- Make sure that pfSense is sending its logs to your Graylog instance, most likely using syslog.
- Add an input into Graylog that accepts the logs from PFSense
- Load the extractors and the content pack into Graylog. 
- Ensure that the elasticsearch instance is parsing the `data-lenght` field as the type 'long'
- Add a new data source in grafana that grabs data from the elasticsearch instance (the url will be http://elasticsearch:9002 with the default config here)
- Load the Grafana dashboard configuration


Sources I used for help with this:
- [Parse and Visualize pFsense Firewall Logs for Free using Graylog and Grafana](https://youtu.be/YkeN7AFs2XQ)
- [Write Your Own Graylog Extractors For pfSense Using Regex](https://youtu.be/XVTQh1WbPek) (very helpful, lead me to writing all my own extractors)
- [Elasticsearch Query Editor](https://youtu.be/hEztaMtobXw)
