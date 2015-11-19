# pjek-monitor

A simple cron-based monitoring tool.

## Verifications

### Docker containers

Given a list of docker containers verifies that all of them are running.

### Disk usage

Alerts if disk usages goes over a configured threshold.

### Load average

Alerts if the 5 minutes load average is over a configured threshold.

### Assertions against logstash queries

E.g. verify no matches for the string 'ERROR' in all log files the last 5 minutes or that the string 'successful' 
appeared at least 3 times.

(Currently hardcoded for the ELK-stack running in a docker container and doing the queries through docker exec)


## Build instructions

<code>$ docker run --rm -v "$PWD":/usr/src/pjek-monitor -w /usr/src/pjek-monitor golang:1.5.1 go build -v</code>


## Running

The application assumes the **config.json** file is in the current directory when the application is started. I.e.
run it like:

<code>$ cd pjek-monitor && ./pjek-monitor</code>

I run it from cron with the following cron line:

<code>*/5 *  *   *   *     cd /root/pjek-monitor && ./pjek-monitor</code>

## TODO

* Allow running in daemon mode
* Make the verifications, especially the logstash queries, a bit more generic and less tied to my specific setup
* Mail support both through local MTA or direct through remote SMTP server

## License

The MIT License (MIT)


