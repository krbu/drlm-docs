Client Configurations Examples
==============================

You can create a configuration file for each client in the /etc/drlm/clients/client_name.cfg.d/ directory. The configuration file must have the extension .cfg.

The following examples show how to create a configuration file for the client performing different types of backups and using different backup options.


Incremental Client Backup
-------------------------

This configuration example demonstrates how to perform a data backup of the /home directory of the client.
  
To use this example, create a config file ``config_name.cfg`` into the /etc/drlm/clients/client_name.cfg.d/ directory and then execute the following command to initiate the backup:

::

  drlm runbackup -c client_name -C config_name

This backup is incremental, so if you run again runbackup only the files that
have changed will be transferred.

.. code-block:: bash

  DRLM_BKP_TYPE=DATA

  # ================================
  # ===== Incremental Backups ======
  # ================================

  # DRLM_INCREMENTAL by default incremental backups are disables. Put
  # this var to "yes" in order to enable
  #
  DRLM_INCREMENTAL="yes"

  # DRLM_INCREMENTAL_HIST defines how many snaps to save
  #
  #DRLM_INCREMENTAL_HIST=6

  # DRLM_INCREMENTAL_BEHAVIOR 
  # 0 - Always incremental. When DRLM_INCREMENTAL_HIST is exceeded deletes the oldest snap. HISTBKPMAX is ignored.
  # 1 - New and empty DR File. When DRLM_INCREMENTAL_HIST is exceeded makes a New and empty DR File before runbackup
  # 2 - New inherited DR File. When DRLM_INCREMENTAL_HIST is exceeded makes a New DR File from last backup. 
  #
  #DRLM_INCREMENTAL_BEHAVIOR=1

  ##################################
  # Additional ReaR Configurations #
  ##################################

  # ================================
  # ========== Data Only ===========
  # ================================

  # When DRLM_BKP_TYPE is set to a 'DATA' value
  # only what is specified in BACKUP_PROG_INCLUDE will be in the backup
  # but not implicitly also all local filesystems as defined in mountpoint_device:
  #
  BACKUP_PROG_INCLUDE=( '/home' )

PXE Client Backup
-----------------

This configuration example demonstrates how to perform a PXE backup of the client. Once the backup is completed, all the staff to perform a PXE restore will be available in the DRLM server automatically.

You can boot from the network and restore the client from the DRLM server.

.. code-block:: bash

  DRLM_BKP_TYPE=PXE

Backup Policy
-------------

This configuration example shows how to back up the client using a backup policy. A backup policy is a set of rules that define which backups to preserve.

In this example, the backup policy will keep the last 15 daily backups, the last 8 weekly backups (on the last day of the week), the last 6 monthly backups(on the last Sunday of the month), and the last 4 yearly backups (on the last Sunday of the year).

::

  # Example of Backup Policy Rules
  BKP_POLICY_RULES=( 
    '15 day'
    '8 week'
    '6 month Sun'
    '4 year Sun'
  )

  BKP_POLICY_AUTO_APPLY="true"  # (Apply the backup policy rules automatically)

