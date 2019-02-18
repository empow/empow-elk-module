# Empow Module README


## Configuration

In order to use empow module, one should first register (for free) to Empow classification center (https://...)
The following set of products are currently supportted (more products will be supportted in the future):
Snort IDS
Paloalto IDS
...

Besides of common module variables (see the official Logstash documentation), the following varibles should 
For each product one configured:
empow.var.input.YYYY.port=XXXX - the listening syslog UDP port number (where YYYY is the product name and XXXX is the port number)
empow.var.internal.networks=XXXX - The list of internal networks (e.g. empow.var.internal.networks='["10.0.1.0/24", "132.68.0.0/16"]')

### Launching from the command-line

```
$LS_HOME/bin/logstash --modules empow -M empow.var.input.snort.port=XXXX -M empow.var.internal.networks='["10.0.1.0/24", "132.68.0.0/16"]'
```

### Adding to `logstash.yml`

Ensure these lines are properly added to your `logstash.yml`:

```
modules:
  - name: empow
    var.input.snort.port: XXXX
    empow.var.internal.networks='[net1, net2, ...]'
```

With this properly configured, when Logstash is started, it will run the module.
