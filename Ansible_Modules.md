## Most commly use ansible modules:

        - ping
        - setup
        - yum
        - yum_repository
        - service
        - package
        - systemd
        - cron
        - lvg
        - lvol
        - parted
        - template
        - fetch
        - register
        - user
        - group
        - authorized_key
        - linefile
        - firewalld
        - nmcli
        - sefcontext
        - selinux
        - command
        - file
        - filesystem
        - mount
        - debug

---
### To Check modules via ansible doc

    ansible-doc --help
    ansible-doc -l
    ansible-doc -l | grep httpd
    ansible-doc -l | grep win
    ansible-doc -l | grep ping
    ansible-doc -l | grep file
    ansible-doc -l | grep copy
    ansible-doc -l | grep lvol
    ansible-doc -l | grep yum

---    

