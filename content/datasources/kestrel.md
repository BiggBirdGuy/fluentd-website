#Collecting Data from Kestrel

##Scenario

You run Kestrel as a message queue and now want to send the messages into various other systems. One way to achieve this is by sending messages through Fluentd.

The benefit of this approach is:

1. No need to gut out the existing Kestrel instances.
2. Take advantage of Fluentd's rich set of output plugins. For example, sending data from Kestrel to both HDFS and Amazon S3.

##Setup

1. Install the [Kestrel input plugin](https://github.com/fluent/fluent-plugin-kestrel) by running the following command

    ```
    $ fluent-gem install fluent-plugin-kestrel
    ```

2. Open your Fluentd configuration file and add the following lines:

    ```
    <source>
      type kestrel
      host localhost     # (required) kestrel host
      queue fluent       # (required) kestrel queue name
      tag kestrel.log    # (required) fluentd tag

      port 22133         # (optional) kestrel port. default 22133
      timeout 10         # (optional) default 10.
    </source>    
    ```
    
