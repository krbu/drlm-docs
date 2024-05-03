DRLM Installation
=================

It is assumed that you have performed a minimal installation of the selected distribution, **dedicated exclusively** to running the DRLM server to avoid interference with existing services.

To install DRLM, execute the following command in the terminal as the root user and follow the spteps. Once completed, you will have a fully functional DRLM server.

.. code-block:: bash

  bash < <(curl -sSL https://drlm.org/install.sh)

If the installation fails you can try the `DRLM Step by Step Installation <./manual_Install.html>`_ to find out where it fails and/or report the error to `DRLM Contributing <./About.html#contributing>`_
 

Supported OS versions
~~~~~~~~~~~~~~~~~~~~~

* Debian 12 (Bookworm)
* Debian 11 (Bullseye)
* Debian 10 (Buster)
* Ubuntu 24.04 (Noble Numbat)
* Ubuntu 22.04 LTS (Jammy Jellyfish)
* Ubuntu 20.04 LTS (Focal Fossa)
* CentOS 8
* Rocky 9
* Rocky 8
* RHEL 9
* RHEL 8
* OpenSUSE Leap 15
* SLES 15
* SLES 12


Firewalld Configuration
~~~~~~~~~~~~~~~~~~~~~~~

It is not strictly necessary, but to simplify the installation process, SELinux and Firewalld will be disabled in this automatic installation process. SELinux and Firewalld can be configured to work seamlessly with the DRLM server, but this configuration will not be covered in this guide.

DRLM uses DHCP, NFS, TFTP, RSYNC and HTTPS. If you want to enable Firewalld, you must accept connections on the following ports

 - `69/tcp`  (Used for TFTP)
 - `69/udp`  (Used for TFTP)
 - `443/tcp` (Used for DRLM API)
 - `873/tcp` (Used for RSYNCD)
