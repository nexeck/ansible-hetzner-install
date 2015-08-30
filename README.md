Hetzner Install
=========

Install Hetzner Server from Rescue System with Ansible

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Install Hetzner Server
        hosts: hetzner

        roles:
            - role: hetzner-install
            binary: /root/.oldroot/nfs/install/installimage
            boot_loader: grub
            raid:
                active: 'no'
                level: 1
            disks:
                - sda
                - sdb
            image: /root/images/Ubuntu-1404-trusty-64-minimal.tar.gz
            partitions:
                - /boot:ext2:512M
                - lvm:vgos:40G
                - lvm:vgsas:all
            logical_volumes:
                - vgos:root:/:ext4:21G
                - vgos:swap:swap:swap:4G
                - vgos:tmp:/tmp:xfs:5G
                - vgos:images:/images:ext4:10G
            format_second: 'no'
            hostname: host.domain.tld
            key_url: https://gist.githubusercontent.com/asdasd.txt
