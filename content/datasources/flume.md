#Collecting Data from Flume

##Scenario

You already have an exiting installation of Flume but want to collect data into backend other than HDFS (for which Flume is optimized).

The benefit of this approach is:

1. No need to gut out the existing Flume instances.
2. Take advantage of Fluentd's rich set of output plugins. For example, sending data to both HDFS and Amazon S3.

##Setup

1. Install the [Flume input plugin](https://github.com/fluent/fluent-plugin-flume) by running the following command

    ```
    $ fluent-gem install fluent-plugin-flume
    ```

2. Open your Fluentd configuration file and add the following lines:

    ```
    <source>
        type flume
        bind YOUR_FLUME_SERVER_HOST
        port YOUR_FLUME_PORT 
    </source>
    ```
    By default, `bind` is localhost and `port` is 56789.
