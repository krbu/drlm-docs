DRLM Quick Start Guide
======================

DRLM Installation
~~~~~~~~~~~~~~~~~~~~~~~~

Follow the steps at `DRLM Installation <./Install.html#drlm-installation>`_. (Select your OS)


Add Network to DRLM Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First of all we must add the network where the ReaR clients are. To do this we have to use the command "drlm addnetwork" with the parameters -n "Network Name", -s "Server IP", -m "Netmask" and -g "Gateway IP".

::

    $ drlm addnetwork -n BuLan -s 192.168.1.38  -m 255.255.255.0 -g 192.168.1.1 


Add Client to DRLM Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now we can add a ReaR client with the command "drlm addclient" and the parameters -i "Client IP", -c "ReaR client hostname" and -I to automatically install ReaR client.

::

    $ drlm addclient -i 192.168.1.45/24 -c ReaRCli1 -I


Run Client Backup
~~~~~~~~~~~~~~~~~

We are ready to take OS backups!!! At this point we have the DRLM server and ReaR client configured, you just have to run the command "drlm runbackup" with the parameter -c "ReaR client host name"

::

    $ drlm runbackup -c ReaRCli1


Restore Client Backup
~~~~~~~~~~~~~~~~~~~~~

Follow the steps at `DRLM Client Recover <./Restore.html>`_.
