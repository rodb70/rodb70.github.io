---
title:  Installing PlantUml picoweb as a service
layout: post
tags: Linux, Mint Linux 20, Cinnamon, plantuml, systemd
---

## Setting up Plantuml picoweb service

I have a use for a local plantuml web service.  So I downloaed the latest `plantuml.jar` file from [Plantuml] and proceded to install in on one of my in-house servers.
I setup a directory for it to run in and sym-linked the versioned plantuml jar file to make upgrades easy.

Most Linux servers these days use `systemd` do I needed to firure out how to do this.  I found this [Systemd Service] very helpful in getting the syntax and commands correct to install a new service.
I also looked at [Run java under systemd] to ensure I was setting up the java server correctly.  I noted that Java is installed in a different location to the example on my system.

My service file `/etc/systemd/system/plantuml-picoweb.service` ended up looking like this:
```
[Unit]
Description=Plantuml picoweb service
After=network.target
StartLimitIntervalSec=1

[Service]
WorkingDirectory=/opt/plantuml
Type=simple
Restart=on-failure
RestartSec=10
User=plantuml
ExecStart=/usr/bin/java -Xms128m -Xmx1024m -jar plantuml.jar -picoweb:3128

[Install]
WantedBy=multi-user.target
```

I had some problems getting the service to start and eventually I traced to down to a syntax error in this file.

I used commands:

`systemctl daemon-reload` to reload the systemd rules after editing this file.

`systemctl start plantuml-picoweb` to start the new service

`systemctl status plantuml-picoweb` to view the startus of the new service

`journalctl -u plantuml-picoweb` to view the log of what systemd was doing with my serice.

After gettting the service to run as I expected I used `systemctl enable plantuml-picoweb` to enable the service to run at start up.


[Plantuml]:https://plantuml.com/download
[Run java under systemd]:https://computingforgeeks.com/how-to-run-java-jar-application-with-systemd-on-linux/
[Systemd Service]:https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6
