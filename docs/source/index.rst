About DRLM Docs
===============

DRLM Docs contains comprehensive documentation on the DRLM (Disaster Recovery Linux Manager). This page describes documentation’s licensing, editions, and versions, and describes how to contribute to the DRLM Docs.

For more information on DRLM, see `About DRLM Project <http://drlm.org>`_. To download DRLM, see the downloads page.

Product Features
----------------

The following features are supported on the most recent releases of
DRLM. Anything labeled as (NEW!) was added as the most recent
release. New functionality for previous releases can be seen in the next
chapter that details each release.

  * Hot maintenance capability. A client backup can be made online
    while the system is running.

  * Command line interface. DRLM does not require a graphical
    interface to run. (console is enough).

  * Multiarch netboot client support (x86_64-efi, i386-efi, i386-pc, powerpc-ieee1275)

  * Automatic client installation from DRLM server

  * Parallel backups

  * Error reporting support to:

      - HP OpenView

      - Nagios (NSCA, NSCA-ng & NRDP)

      - Zabbix

      - Mail

      - XML/JSON

      - Telegram

  * Centralized backup scheduling with a job scheduler and backup policy

  * Export and Import backup between DRLM servers or DRLM clients

  * Real time clients log in DRLM server

Contents:
=========

.. toctree::
   :maxdepth: 2
   :caption: User Documentation

   QuickStart
   Install
   manual_Install
   Restore
   ErrorReporting

.. toctree::
   :maxdepth: 2
   :caption: Command Reference

   overview
   network_opers
   client_opers
   backup_opers

.. toctree::
   :maxdepth: 2
   :caption: Client Configuration

   client_config_default
   multiple_client_config
   cluster_client_config
   client_config_examples

.. toctree::
   :maxdepth: 2
   :caption: DRLM SERVICES

   drlm_api
   drlm_proxy
   drlm_stord
   drlm_rsyncd
   drlm_tftpd

.. toctree::
   :maxdepth: 2
   :caption: Developer Documentation

   building_grub2

.. toctree::
   :maxdepth: 1
   :caption: About Documentation

   About

