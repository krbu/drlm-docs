DRLM STUNNEL
============

DRLM stunnel server daemon. Used to secure the rsync transport over TLS.
This is the new default, so all backups/restores will be encripted in tansport.


Configuration
~~~~~~~~~~~~~

.. code-block:: bash

  pid = /var/run/stunnel.pid
  foreground = yes
  debug = debug
  output = /var/log/drlm/drlm-stunnel.log
  TIMEOUTclose = 1
  verify = 1
  options = NO_SSLv3
  sslVersionMin = TLSv1.2
  sslVersionMax = TLSv1.3
  socket = l:TCP_NODELAY=1
  socket = r:TCP_NODELAY=1

  [rsync]
  accept = 0.0.0.0:874
  connect = 0.0.0.0:873
  CApath = /etc/drlm/cert
  cert = /etc/drlm/cert/drlm.crt
  key = /etc/drlm/cert/drlm.key
  client = no


Management
~~~~~~~~~~

Start DRLM STUNNEL

.. code-block:: console
 
  ~# systemctl start drlm-stunnel.service

Restart DRLM RSYNCD

.. code-block:: console

  ~# systemctl restart drlm-stunnel.service

Stop DRLM RSYNCD

.. code-block:: console

  ~# systemctl stop drlm-stunnel.service

Log File
~~~~~~~~

The log file for DRLM STUNNEL can be found at /var/log/drlm/drlm-stunnel.log

example:

.. code-block:: console

  root@drlmsrv:~# cat /var/log/drlm/drlm-stunnel.log 
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS read client hello                                                                                                                                        
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write server hello                                                                                                                                       
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write change cipher spec                                                                                                                                 
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): TLSv1.3 write encrypted extensions                                                                                                                                 
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write certificate request                                                                                                                                
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write certificate                                                                                                                                        
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): TLSv1.3 write server certificate verify                                                                                                                            
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write finished                                                                                                                                           
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): TLSv1.3 early data                                                                                                                                                 
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): TLSv1.3 early data                                                                                                                                                 
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS read client certificate                                                                                                                                  
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS read finished                                                                                                                                            
  2024.08.29 06:09:13 LOG7[5]:      6 server accept(s) requested                                                                                                                                                      
  2024.08.29 06:09:13 LOG7[5]:      6 server accept(s) succeeded                                                                                                                                                      
  2024.08.29 06:09:13 LOG7[5]:      0 server renegotiation(s) requested                                                                                                                                               
  2024.08.29 06:09:13 LOG7[5]:      0 session reuse(s)                                                                                                                                                                
  2024.08.29 06:09:13 LOG7[5]:      5 internal session cache item(s)                                                                                                                                                  
  2024.08.29 06:09:13 LOG7[5]:      0 internal session cache fill-up(s)                                                                                                                                               
  2024.08.29 06:09:13 LOG7[5]:      0 internal session cache miss(es)
  2024.08.29 06:09:13 LOG7[5]:      0 external session cache hit(s)
  2024.08.29 06:09:13 LOG7[5]:      0 expired session(s) retrieved
  2024.08.29 06:09:13 LOG7[5]: Generate session ticket callback
  2024.08.29 06:09:13 LOG7[5]: Initializing application specific data for session authenticated
  2024.08.29 06:09:13 LOG7[5]: Deallocating application specific data for session connect address
  2024.08.29 06:09:13 LOG7[5]: New session callback
  2024.08.29 06:09:13 LOG6[5]: No peer certificate received
  2024.08.29 06:09:13 LOG6[5]: Session id: 6BC58C768B7DA65289449588CA1F06DA2A42B2F5402B8FB99102FE104678670D
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write session ticket
  2024.08.29 06:09:13 LOG7[5]: Initializing application specific data for session authenticated
  2024.08.29 06:09:13 LOG7[5]: Deallocating application specific data for session connect address
  2024.08.29 06:09:13 LOG7[5]: Generate session ticket callback
  2024.08.29 06:09:13 LOG7[5]: Initializing application specific data for session authenticated
  2024.08.29 06:09:13 LOG7[5]: Deallocating application specific data for session connect address
  2024.08.29 06:09:13 LOG7[5]: New session callback
  2024.08.29 06:09:13 LOG6[5]: No peer certificate received
  2024.08.29 06:09:13 LOG6[5]: Session id: 9EC5C4AFF88455624198DE99B614F3738DD2DCFFAC52CA63833FF4201DFA9E0F
  2024.08.29 06:09:13 LOG7[5]: TLS state (accept): SSLv3/TLS write session ticket
  2024.08.29 06:09:13 LOG6[5]: TLS accepted: new session negotiated
  2024.08.29 06:09:13 LOG6[5]: TLSv1.3 ciphersuite: TLS_AES_256_GCM_SHA384 (256-bit encryption)
  2024.08.29 06:09:13 LOG6[5]: Peer temporary key: X25519, 253 bits
  2024.08.29 06:09:13 LOG7[5]: Compression: null, expansion: null
  2024.08.29 06:09:13 LOG6[5]: s_connect: connecting 0.0.0.0:873
  2024.08.29 06:09:13 LOG7[5]: s_connect: s_poll_wait 0.0.0.0:873: waiting 10 seconds
  2024.08.29 06:09:13 LOG7[5]: FD=6 events=0x2001 revents=0x0
  2024.08.29 06:09:13 LOG7[5]: FD=11 events=0x2005 revents=0x1
  2024.08.29 06:09:13 LOG5[5]: s_connect: connected 0.0.0.0:873
  2024.08.29 06:09:13 LOG6[5]: persistence: 0.0.0.0:873 cached
  2024.08.29 06:09:13 LOG5[5]: Service [rsync] connected remote server from 127.0.0.1:45440
  ...
  ...
  ...
