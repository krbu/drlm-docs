Multiple Client Configurations
==============================

DRLM supports multiple client configurations. This is useful when you have multiple clients that need to be backed up to the same server, but have different backup requirements. 

For example, you may have a client that OS needs to be backed up weekly, but some data of this client needs to be backed up daily. 

You can create a separate configuration for the OS and data client, and then use the `--config` option to specify which configuration to use when running the `drlm runbackup` command. 
If no configuration is specified, the default (/etc/drlm/clients/client_name.cfg) configuration will be used.

To create a new client configuration, copy the default configuration file to a new file in the `/etc/drlm/clients/client_name.cfg.d/` directory, and then modify the new file as needed.

For example, to create a new configuration for a client named `client2`, you would copy the default configuration file to a new file named `/etc/drlm/clients/client2.cfg.d/data.cfg`, and then modify the new file as needed.

When you run the `drlm runbackup` command, you can specify the configuration to use with the `--config` option. For example:

::
  
  drlm runbackup -c client2 --config data


This will use the `/etc/drlm/clients/client2.cfg.d/data.cfg` configuration file for the backup.

You can also add jobs to the new configuration file using the `drlm addjob` command. For example:

::

  drlm addjob -c client2 -s 2017-02-03T08:00 -e 2024-04-05T23:00 -r 1day --config data



