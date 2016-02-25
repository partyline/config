## use the phone as a 3g modem

In the phone settings: General > Tethering & network > USB tethering.
Plug the cable, interface cdce0 should appear in `ifconfig`.

```
echo "dhcp" > /etc/hostname.cdce0
/etc/netstart /etc/hostname.cdce0
```
That's, it. Alternatively use `dhclient cdce0`.

## file transfer

```
pkg_add libmtp
mtp-detect
mtp-connect --sendfile file
mtp-filetree
```
