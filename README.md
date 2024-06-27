rpi_wifi_usb
============

This role configures i.e. a Raspberry Pi zero W as a "SMB/CIFS Wifi USB Drive". It creates a image file which serves as storage for the drive and includes a watchdog which mounts and unmounts the "USB Drive" from the host if files get manipulated over wifi.

Thanks to [davidhoness](https://gist.github.com/davidhoness/) for the [gist of the watchdog](https://gist.githubusercontent.com/davidhoness/0f45ef6a41bac6311614f109acbf92db/raw/970badd0ae4b097e3af8d5142e65c34b21f5cfab/usb_share.py).

As always: Use at your own risk!

Role Variables
--------------

| Name                    | Comment                                             | Default value                |
|-------------------------|-----------------------------------------------------|------------------------------|
| usb_share_file          | Location of the USB image file                      | `/piusb.bin`                 |
| usb_share_space         | Size of the USB image file                          | `4G`                         |
| usb_share_path          | Mount point of the USB image file                   | `/mnt/wifi_usb_share`        |
| usb_share_watchdog_path | Base path for the watchdog                          | `/opt/rpi_wifi_usb_watchdog` |
| raspberry_pi_boot_dev   | Raspberry pi boot dev (used for editing config.txt) | `/dev/mmcblk0p1`             |

Example Playbook
----------------
```yaml
- name: Raspberry Pi Wifi USB stick
  hosts: wifi_usb
  roles:
    - role: oxivanisher.raspberry_pi.rpi_wifi_usb_smb                 # configure rpi wifi usb
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.raspberry_pi](https://galaxy.ansible.com/ui/repo/published/oxivanisher/raspberry_pi/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-raspberry_pi).
