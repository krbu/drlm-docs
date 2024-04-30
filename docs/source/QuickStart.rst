DRLM Quick Start Guide
======================

DRLM Installation
~~~~~~~~~~~~~~~~~~~~~~~~

Download, build and install DRLM from source code. (For more information, see `DRLM Installation <./Install.html>`_)

.. code-block:: bash

  ~# bash < <(curl -sSL https://drlm.org/install.sh)

.. note:: 
  It is assumed that you have performed a minimal installation of the selected distribution, **dedicated exclusively** to running the DRLM server.

Add Client to DRLM Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once the DRLM server is installed we can add clients with the command ``drlm addclient`` and the parameters ``-i <Client IP>``, ``-c <Client name>``

To install the client automatically, you can use the ``-I`` parameter. This is why the client must be accessible via SSH. By default the root user is used, but you can specify another user with the ``-u <user>`` parameter. This user needs administrator privileges.

.. code-block:: console

  ~# drlm -v addclient -i 192.168.181.53 -c ReaRCli1 -I


Run Client Backup
~~~~~~~~~~~~~~~~~

We are ready to take OS backups!!! 

At this point we have the DRLM server and client configured, you just have to run the command ``drlm runbackup`` with the parameter ``-c <Client name``

.. code-block:: console

    ~# drlm -v runbackup -c ReaRCli1

List Clients & Backups
~~~~~~~~~~~~~~~~~~~~~~

To list the clients and their backups, you can use the command ``drlm listclient`` and ``drlm listbackup``

.. code-block:: console

    ~# drlm listclient
    ~# drlm listbackup

Restore Client Backup
~~~~~~~~~~~~~~~~~~~~~

Follow the steps at `DRLM Client Recover <./Restore.html>`_.
