# Preflight checks

Make the following checks to validate that this example can work against your environment.

## Set proper HBase version

Check the Master WebUI or use `curl` to get the HBase version and validate that the version in pom.xml for
`hbase-shaded-client` is accurate.

```
$ curl http://localhost:16010/version
```

## Update repository location

Update the repository `url` to be the hostname for your HBase master.

```
    <repository>
      <id>hbase-webui-maven-repo</id>
      <url>http://<correct-hostname-here>:16010/static/maven-repo/</url>
      <name>Maven repository exposed by HBase Master WebUI</name>
    </repository>
```

# Build the exemplar

Build the example:
```
$ mvn package
```

# Run the exemplar

Run the SQL and NoSQL examples:

```
$ mvn exec:exec -Dexec.executable=java -Dexec.args="-cp target/libs/*:target/hbase-client-webui-maven-0.0.1-SNAPSHOT.jar:$HBASE_CONF_DIR com.github.joshelser.hbase.Client"
```
