# Apache Hadoop 2.7.1 in a Docker container

Hadoop in a pseudo distributed mode in a Docker container, forked from [sequenceiq](https://github.com/ouyi/hadoop-docker). The changes are:

- Change core-site.xml to use 0.0.0.0 as the interface to bind to instead of the hostname (to allow for external access)

## Start a container

**Make sure that SELinux is disabled on the host. If you are using boot2docker you don't need to do anything.**

```
docker run -P -it farberg/hadoop-docker /etc/bootstrap.sh -bash
```

## Testing

You can run one of the stock examples:

```
cd $HADOOP_PREFIX
# run the mapreduce
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.1.jar grep input output 'dfs[a-z.]+'

# check the output
bin/hadoop fs -cat output/{*}
```
