DRLM server (internal) backups
==============================

This feature allows DRLM to manage its own configuration backups simplifying the recovery process for DRLM configurations and providing Full DR of the DRLM server.

All the setup is already done, and backup jobs created (disabled by default).

DRLM internal client
--------------------

DRLM server internal (self) client.

::

  :~# drlm listclient -c internal
  Id   Name       MacAddres     Ip               Client OS     ReaR Version    Network  Scheduled  VIP
  0    internal                 127.0.0.1        Debian 12.6   2.7/Git         lo       false

DRLM internal backup jobs
-------------------------

Pre-configured backup jobs for configuration files (default) and Full ISO DR of the server (iso).

.. note::

  The jobs are disabled by default. Just enable them if default schedules are ok, or re-schedule
  if needed.

::

  :~# drlm listjob -c internal
  Id  Status     Client    Last Date         Next Date          Repeat   Configuration       
  2   Disabled   internal                    2024-09-04T08:00   1day     default             
  3   Disabled   internal                    2024-09-06T12:00   1month   iso  

Configuration 
-------------

Configuration backups location is: /etc/drlm/clients/internal.cfg. Can be customized to your needs.

::

  DRLM_BKP_TYPE=DATA
  BACKUP_ONLY_INCLUDE="yes"
  BACKUP_PROG_INCLUDE+=( '/etc/drlm/' )
  BACKUP_PROG_INCLUDE+=( '/etc/rear/' )
  BACKUP_PROG_INCLUDE+=( '/var/log/drlm/' )
  BACKUP_PROG_INCLUDE+=( '/var/log/rear/' )
  BACKUP_PROG_INCLUDE+=( '/var/lib/drlm/drlm.sqlite' )

Full ISO DR backup location is: /etc/drlm/clients/internal.cfg.d/iso.cfg. Can be customized to your needs.

::

  DRLM_BKP_TYPE=ISO_FULL
  BACKUP_PROG_EXCLUDE+=( '/var/lib/drlm/arch/*' )
  OUTPUT_URL=file:///var/lib/drlm/store/internal/iso
  OUTPUT_PREFIX=ISO
  ISO_FILE_SIZE_LIMIT=0

Run a configuration backup
--------------------------

::

  :~# drlm runbackup -c internal

Run a manual Full ISO DR backup
-------------------------------

::

  :~# drlm runbackup -c internal -C iso

List internal backups
---------------------

::

  :~# drlm listbackup -c internal
  Backup Id           Client Name  Backup Date       Status    Duration   Size        PXE  Config    Type      
  0.20240902143847    internal     2024-09-02 14:38  enabled   0h.0m.17s  269M             default   DATA-RSYNC
  0.20240903024052    internal     2024-09-03 02:40  enabled   0h.4m.31s  3.5G             iso       ISO_FULL-NETFS

Restore DRLM configuration files from backup
--------------------------------------------

.. note::

  By default all restored files will be placed in **/var/tmp/drlm/restored** unless [-O,--overwrite] option is set.

This example shows to restore all [ client1 ] configurations from last internal configuration backup to its default location.

::

  :~# drlm restore -c internal --files /etc/drlm/clients/client1.cfg,/etc/drlm/clients/client1.cfg.d --overwrite

Restore DRLM server from scratch
--------------------------------

.. important::

  To be able to recover DRLM server from scratch, you need to download the ISO file in **/var/lib/drlm/store/internal/iso/ISO/**
  to a safe location.

.. note::

  All client backups are excluded by default to prevent a huge ISO image creation. You can customize the configuration to
  suit your needs and include some critical backups to recover fast.

To recover a DRLM server from scrath just need to boot from the ISO image. After booting it will perform an unattended recover of the server.

