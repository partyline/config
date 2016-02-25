```
ftp http://ftp.fr.openbsd.org/pub/OpenBSD/snapshots/amd64/install59.fs
dd if=install59.fs of=/dev/rsda1c bs=16M
```
Press 'f2' to enter bios settings, disable secure boot, enable legacy (CSM).
Save and exit, press 'esc' and choose boot from USB disk.

## full disk encryption
