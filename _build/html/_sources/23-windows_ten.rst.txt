===================
Linux in WIndows 10
===================

To mount a smb shared drive :

* Create a mount point in ``/mnt`` : ``mkdir /mnt/shared``
* Mount the drive : ``sudo mount -t drvfs '\\10.40.63.20\shared' /mnt/shared``
