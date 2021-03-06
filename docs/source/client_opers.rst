Client Operations
=================

DRLM client operations allow us to add, remove, modify and
list clients of database.

Add Client
----------

This command is used to add clients to DRLM database. It is
called like this::

   $ drlm addclient [options]

If the client you wish to add is online (network reachable), you will only need to set its IP in CIDR notation in order to add it to the database. It will then automatically fetch and prompt all the required client parameters (hostname, network and MAC address), leaving to you the option to keep and save those parameters or to enter them manually in case you refuse.

In this case, the :program:`drlm addclient` has the following required options:

.. program:: `drlm addclient`

.. option:: -i ip_in_CIDR_format, --ipaddr ip_in_CIDR_format

 Examples::

   $ drlm addclient -i 192.168.0.15/24

 If the :program:`drlm addclient` does not correctly fetch the client's hostname, you can set it manually in the same command.

 Examples::

   $ drlm addclient -i 192.168.0.15/24 -c rear-debian

.. option:: -I, --installclient

 If the client is network reachable you can also automatically install the client when is added to DRLM.
 So in only one command the client is added and installed.
 Installclient have additional options than you can add behind the -I. For more information about Installclient read the "Install Client" section.

 Examples::

   $ drlm addclient -i 192.168.0.15/24 -I
   $ drlm addclient -i 192.168.0.15/24 -c rear-debian -I
   $ drlm addclient -i 192.168.0.15/24 -c rear-debian -I -u root -U http://url.to.rear/download

If the client is not network reachable when you want to register it in the database or you wish to manually enter all the required parameters, you can do it with the required options available:

.. program:: `drlm addclient`

.. option:: -c client_name, --client client_name

   Set the client's name.

   .. note::

      It is not mandatory, but recommended that the client_name is the same as the client hostname.

.. option:: -i ip, --ipaddr ip

   Client IP address (not in CIDR notation if you are manually adding all the required parameters).

.. option:: -M mac_address, --macaddr mac_address

   Client MAC address.

.. option:: -n network_name, --netname network_name

   Client NETWORK.

   Examples::

   $ drlm addclient -c clientHost1 -M 00-40-77-DB-33-38 -i 13.74.90.10 -n vlan12
   $ drlm addclient --client clientHost1 --macaddr 00-40-77-DB-33-38 -i 13.74.90.10 -n vlan12

   .. warning::

      If the network_name doesn't exist in DRLM database you will get an error. First
      of all register the network where the client will be registered.

Help option:

.. option:: -h, --help

   Show drlm addclient help.

   Examples::

   $ drlm addclient -h
   $ drlm addclient --help


Install Client
--------------

This command is used to install and configure DRLM and ReaR on a remote
Server. It is called like this::

   $ drlm instclient [options]

The :program:`drlm instclient` has some requiered options:

.. program::  `drlm instclient`

.. option:: -c client_name, --client client_name

   Select Client name to add.

.. option:: -I client_id, --id client_id

   Client Id.

Additional options:

.. option:: -u user, --user user

   User with admin privileges to install and configure software

   .. note:: if not user is specified root will be used.

.. option:: -U url_rear, --url_rear url_rear

   rpm or deb package for specific distro. For example http://download.opensuse.org/repositories/Archiving:/Backup:/Rear/Debian_7.0/all/rear_1.17.2_all.deb

   .. note:: If not url is specified will be used the package defined in "REAR DEB PACKAGE URL" section of /usr/share/drlm/conf/default.conf

   Examples::

   $ drlm instclient -c ReaRCli1 -u admin -U http://download.opensuse.org/repositories/Archiving:/Backup:/Rear/Debian_7.0/all/rear_1.17.2_all.deb
   $ drlm instclient -c ReaRCli2

Help option:

.. option:: -h, --help

   Show drlm instclient help.

   Examples::

   $ drlm instclient -h

Delete Client
-------------

This command is used to delete clients from DRLM database. It is
called like this::

   $ drlm delclient [options]

The :program:`drlm delclient` has some required options:

.. program:: `drlm delclient`

.. option:: -c client_name, --client client_name

   Select Client to delete by NAME.

.. option:: -I client_id, --id client_id

   Select Client to delete by ID.

   Examples::

   $ drlm delclient -c clientHost1
   $ drlm delclient --client clientHost1
   $ drlm delclient -I 12
   $ drlm delclient --id 12


Help option:

.. option:: -h, --help

   Show drlm delclient help.

   Examples::

   $ drlm delclient -h
   $ drlm delclient --help

Modify Client
-------------

This command is used to modify clients from DRLM database. It is
called like this::

   $ drlm modclient [options]

The :program:`drlm modclient` has some required options:

.. program:: `drlm modclient`

.. option:: -c client_name, --client client_name

   Select Client to change by NAME

.. option:: -I client_id, --id client_id

   Select Client to change by ID


Additional options:

.. option:: -i ip, --ipaddr ip

   Set new IP address to client.

   Examples::

   $ drlm modclient -c clientHost1 -i  13.74.90.10

.. option:: -M mac_address, --macaddr mac_address

   Set new MAC address to client.

   Examples::

   $ drlm modclient -c clientHost1 -M  00-40-77-DB-33-38
   $ drlm modclient --client clientHost1 --macaddr  00-40-77-DB-33-38
   $ drlm modclient -I 12 --macaddr 00-40-77-DB-33-38
   $ drlm modclient --id 12 -M 00-40-77-DB-33-38

.. option:: -n network_name, --netname network_name

   Assign new NETWORK to client.

   Examples::

   $ drlm modclient -c clientHost1 -n  vlan12
   $ drlm modclient --client clientHost1 --netname  vlan12
   $ drlm modclient -I 12 --netname vlan12
   $ drlm modclient --id 12 -n vlan12

Help option:

.. option:: -h, --help

   Show drlm modclient help.

   Examples::

   $ drlm modclient -h
   $ drlm modclient --help

List Clients
------------

This command is used to list the clients stored at the database.
It is called like this::

   $ drlm listclient [options]

The :program:`drlm listclient` has some options:

.. program:: `drlm listclient`

.. option:: -c client_name, --client client_name

   Select Client to list.

   Examples::

   $ drlm listclient -c clientHost1
   $ drlm listclient --client clientHost1

.. option:: -A, --all

   List all clients. This option is set by default if any option is specified.

   Examples::

   $ drlm listclient
   $ drlm listclient -A
   $ drlm listclient --all

Help option:

.. option:: -h, --help

   Show drlm listclient help.

   Examples::

   $ drlm listclient -h
   $ drlm listclient --help
