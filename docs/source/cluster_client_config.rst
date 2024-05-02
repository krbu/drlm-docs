Cluster Client Configuration
============================

DRLM (Disaster Recovery Linux Manager) supports the creation of clients with Virtual IP (VIP) for cluster configurations. 
This feature allows DRLM to manage and interact with multiple nodes in a cluster as if they were a single entity, simplifying the disaster recovery process for clustered environments.

To configure a client with VIP in DRLM, first add each node in the cluster as a separate client in DRLM. 
Then, create a new client with the VIP address and add the previously created clients as nodes to the new client.

To add the nodes to the VIP client, use the `drlm modclient -c cluster-vip -a client_id`.

::

  :~# drlm modclient -c cluster-vip -a 100
  :~# drlm modclient -c cluster-vip -a 101
  :~# drlm modclient -c cluster-vip -a 102

  :~# drlm listclient

  Id   Name           MacAddres     Ip            Client OS     ReaR Version                             Network  Scheduled  VIP             
  100  cluster-node1  01ab23cd45e6  10.10.10.11   Ubuntu 24.04  2.7-git.5341.4f109eb7.master/2023-12-20  ens3     true             
  101  cluster-node2  01ab23cd45e7  10.10.10.12   Ubuntu 24.04  2.7-git.5341.4f109eb7.master/2023-12-20  ens3     true             
  102  cluster-node3  01ab23cd45e8  10.10.10.13   Ubuntu 24.04  2.7-git.5341.4f109eb7.master/2023-12-20  ens3     true             
  103  cluster-vip    01ab23cd45e9  10.10.10.10   Ubuntu 24.04  2.7-git.5341.4f109eb7.master/2023-12-20  ens3     true       100,101,102


This will enable DRLM to recognize the client as a cluster and handle it accordingly.

