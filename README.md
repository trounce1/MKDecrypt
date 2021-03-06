# MKDecrypt(.py)


usage: MKDecrypt.py [-h] [-v] [-r | -w] [-m MOUNTPOINT] FILE MASTERKEY

MKDecrypt.py (Master Key Decryptor) is a python script to assist with
decrypting encrypted volumes using the recovered masterkey for various
truecrypt type encrypted containers. Script should be run as root,
sudo recommended.

positional arguments:
  FILE                  the encrypted container, FILE
  MASTERKEY             the MASTERKEY as a hexadecimal string

optional arguments:
  -h, --help            show this help message and exit
  -v, --verbose         verbose output
  -X  --volatility      specifies that you are using a volatility file instead of hex chars
  -r, --read-only       opens FILE in read only mode (default)
  -w, --read-write      opens FILE in read/write mode
  -m MOUNTPOINT, --mountpoint MOUNTPOINT
                        mount encrypted volume at MOUNTPOINT

Examples: [sudo] ./MKDecrypt.py -m /mnt truecrypt.tc 123...def
          [sudo] ./MKDecrypt.py -v /dev/sdb 123...def


Limitations: May produce false negatives if the filesystem used is not
one of the standard truecrypt/veracrypt formats.  It is designed to
work with standard truecrypt containers and not bootable
pre-authentication bootloader partitions/disks.  The HFS+
implementation is _sketchy_ but appears to work, for now.
Veracrypt now supports 2 new encryption algorithms: Camellia and
Kuznyechik.  Kuznyechik is currently not supported by MKDecrypt.

Requirements:  Linux OS with Python3.x and LVM2 (dmsetup).  It is
preferable to make the script executable before use.
