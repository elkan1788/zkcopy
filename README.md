# zkcopy

Tool for fast copying ZooKeeper data between different clusters.
Originally it was developed for copying big volumes of configuration over WAN.

## Build

Requires [apache maven 3](https://maven.apache.org/).

```bash
mvn clean package
```

## Usage

```bash
java -jar target/zkcopy.jar --source server:port/path --target server:port/path
```
Or
```
java -Dsource="server:port/path" \
     -Ddestination="server:port/path" \
     -Dthreads=10 \
     -DremoveDeprecatedNodes=true \
     -jar target/zkcopy-release-version.jar
```

For [docker](https://hub.docker.com/r/kshchepanovskyi/zkcopy/), use following commands:

```bash
docker pull kshchepanovskyi/zkcopy
docker run --rm -it kshchepanovskyi/zkcopy --source server:port/path --target server:port/path
```
Or
```
docker run --rm -it kshchepanovskyi/zkcopy \
    -Dsource="server:port/path" \
    -Ddestination="server:port/path" \
    -Dthreads=10 \
    -DremoveDeprecatedNodes=true
```

## Options

```
usage: zkcopy
 -c,--copyOnly <true|false>       (optional) set this flag if you do not
                                  want to remove nodes that are removed on
                                  source
 -h,--help                        print this message
 -s,--source <server:port/path>   location of a source tree to copy
 -t,--target <server:port/path>   target location
 -w,--workers <N>                 (optional) number of concurrent workers
                                  to copy data
```