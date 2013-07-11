# OpenShift AeroGear Unified Push Cartridge

Provides the AeroGear Unified Push Server running on top of JBoss Application Server on OpenShift.

## Installation
The AeroGear Unified Push Server defaults to using MySQL. When creating your application, you'll also want to add the MySQL cartridge:

```
rhc app create <APP> ag-unified-push mysql-5.1
```

## Template Repository Layout

    .openshift/        Location for OpenShift specific files
      action_hooks/    See the Action Hooks documentation [1]
      markers/         See the Markers section [2]

\[1\] [Action Hooks documentation](https://github.com/openshift/origin-server/blob/master/node/README.writing_applications.md#action-hooks)
\[2\] [Markers](#markers)


## Environment Variables

The `ag-unified-push` cartridge provides several environment variables to reference for ease
of use:

    OPENSHIFT_AG_UNIFIED_PUSH_IP                         The IP address used to bind JBossAS
    OPENSHIFT_AG_UNIFIED_PUSH_HTTP_PORT                  The JBossAS listening port
    OPENSHIFT_AG_UNIFIED_PUSH_CLUSTER_PORT               
    OPENSHIFT_AG_UNIFIED_PUSH_MESSAGING_PORT             
    OPENSHIFT_AG_UNIFIED_PUSH_MESSAGING_THROUGHPUT_PORT  
    OPENSHIFT_AG_UNIFIED_PUSH_REMOTING_PORT              

For more information about environment variables, consult the
[OpenShift Application Author Guide](https://github.com/openshift/origin-server/blob/master/node/README.writing_applications.md).

## Markers

Adding marker files to `.openshift/markers` will have the following effects:

    enable_jpda          Will enable the JPDA socket based transport on the java virtual
                         machine running the JBoss AS 7 application server. This enables
                         you to remotely debug code running inside the JBoss AS 7
                         application server.

    java7                Will run JBossAS with Java7 if present. If no marker is present
                         then the baseline Java version will be used (currently Java6)
