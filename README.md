# logstash-conf

Just a little repo where I keep/backup my logstash pipeline configs. These additional plugins are needed

* Output
  * [logstash-output-elasticsearch_groom](https://github.com/itzg/logstash-output-elasticsearch-groom)
* Input
  * [logstash-input-heartbeat](https://github.com/logstash-plugins/logstash-input-heartbeat)

...however, I'm actually using the [itzg/logstash](https://registry.hub.docker.com/u/itzg/logstash/) Docker image, which already includes those. I start my container using

```
docker run -d --name logstash --restart=always --link es-00:es \
  -v /var/log:/logs -v $HOME/logstash-conf:/conf -p 25827:25826/udp --log-driver=syslog \
  itzg/logstash
```

where I have another container, `es-00`, that is running the [itzg/elasticsearch](https://registry.hub.docker.com/u/itzg/elasticsearch/) image.
