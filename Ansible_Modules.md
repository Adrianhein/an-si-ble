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

## Example Usage of searching module "copy"
### ansible-doc -l | grep copy
### ansible-doc copy
        [admin@my-infra-01 Practice]$ ansible-doc copy
        > ANSIBLE.BUILTIN.COPY    (/usr/lib/python3.9/site-packages/ansible/modules/copy.py)
        
                The `copy' module copies a file from the local or remote machine to a location on the remote machine. Use the [ansible.builtin.fetch] module to copy files from
                remote locations to the local box. If you need variable interpolation in copied files, use the [ansible.builtin.template] module. Using a variable in the `content'
                field will result in unpredictable output. For Windows targets, use the [ansible.windows.win_copy] module instead.
        
        ADDED IN: historical
        
          * note: This module has a corresponding action plugin.
        
        OPTIONS (= is mandatory):
        
        - attributes
                The attributes the resulting filesystem object should have.
                To get supported flags look at the man page for `chattr' on the target system.
                This string should contain the attributes in the same order as the one displayed by `lsattr'.
                The `=' operator is assumed as default, otherwise `+' or `-' operators need to be included in the string.
                aliases: [attr]
                default: null
                type: str
                added in: version 2.3 of ansible-core
        
        
        - backup
                Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.
                default: false
                type: bool
                added in: version 0.7 of ansible-core
        
        
        - checksum
                SHA1 checksum of the file being transferred.
                Used to validate that the copy of the file was successful.
                If this is not provided, ansible will use the local calculated checksum of the src file.
                default: null
                type: str
                added in: version 2.5 of ansible-core
        
        
        - content
                When used instead of `src', sets the contents of a file directly to the specified value.
                Works only when `dest' is a file. Creates the file if it does not exist.
                For advanced formatting or if `content' contains a variable, use the [ansible.builtin.template] module.
                default: null
                type: str
                added in: version 1.1 of ansible-core
        
        
        - decrypt
                This option controls the autodecryption of source files using vault.
                default: true
                type: bool
                added in: version 2.4 of ansible-core
        
        
        = dest
                Remote absolute path where the file should be copied to.
                If `src' is a directory, this must be a directory too.
                If `dest' is a non-existent path and if either `dest' ends with "/" or `src' is a directory, `dest' is created.
                If `dest' is a relative path, the starting directory is determined by the remote host.
                If `src' and `dest' are files, the parent directory of `dest' is not created and the task fails if it does not already exist.
                type: path
        
        - directory_mode
                When doing a recursive copy set the mode for the directories.
                If this is not set we will use the system defaults.
                The mode is only set on directories which are newly created, and will not affect those that already existed.
                default: null
                type: raw
                added in: version 1.5 of ansible-core
        
        
        - follow
                This flag indicates that filesystem links in the destination, if they exist, should be followed.
                default: false
                type: bool
                added in: version 1.8 of ansible-core
        
        
        - force
                Influence whether the remote file must always be replaced.
                If `true', the remote file will be replaced when contents are different than the source.
                If `false', the file will only be transferred if the destination does not exist.
                default: true
                type: bool
                added in: version 1.1 of ansible-core
        
        
        - group
                Name of the group that should own the filesystem object, as would be fed to `chown'.
                When left unspecified, it uses the current group of the current user unless you are root, in which case it can preserve the previous ownership.
                default: null
                type: str
        
        - local_follow
                This flag indicates that filesystem links in the source tree, if they exist, should be followed.
                default: true
                type: bool
                added in: version 2.4 of ansible-core
        
        
        - mode
                The permissions of the destination file or directory.
                For those used to `/usr/bin/chmod' remember that modes are actually octal numbers. You must either add a leading zero so that Ansible's YAML parser knows it is an
                octal number (like `0644' or `01777') or quote it (like `'644'' or `'1777'') so Ansible receives a string and can do its own conversion from string into number.
                Giving Ansible a number without following one of these rules will end up with a decimal number which will have unexpected results.
                As of Ansible 1.8, the mode may be specified as a symbolic mode (for example, `u+rwx' or `u=rw,g=r,o=r').
                As of Ansible 2.3, the mode may also be the special string `preserve'.
                `preserve' means that the file will be given the same permissions as the source file.
                When doing a recursive copy, see also `directory_mode'.
                If `mode' is not specified and the destination file *does not* exist, the default `umask' on the system will be used when setting the mode for the newly created
                file.
                If `mode' is not specified and the destination file *does* exist, the mode of the existing file will be used.
                Specifying `mode' is the best way to ensure files are created with the correct permissions. See CVE-2020-1736 for further details.
                default: null
                type: raw
        
        - owner
                Name of the user that should own the filesystem object, as would be fed to `chown'.
                When left unspecified, it uses the current user unless you are root, in which case it can preserve the previous ownership.
                Specifying a numeric username will be assumed to be a user ID and not a username. Avoid numeric usernames to avoid this confusion.
                default: null
                type: str
        
        - remote_src
                Influence whether `src' needs to be transferred or already is present remotely.
                If `false', it will search for `src' on the controller node.
                If `true' it will search for `src' on the managed (remote) node.
                `remote_src' supports recursive copying as of version 2.8.
                `remote_src' only works with `mode=preserve' as of version 2.6.
                Autodecryption of files does not work when `remote_src=yes'.
                default: false
                type: bool
                added in: version 2.0 of ansible-core
        
        
        - selevel
                The level part of the SELinux filesystem object context.
                This is the MLS/MCS attribute, sometimes known as the `range'.
                When set to `_default', it will use the `level' portion of the policy if available.
                default: null
                type: str
        
        - serole
                The role part of the SELinux filesystem object context.
                When set to `_default', it will use the `role' portion of the policy if available.
                default: null
                type: str
        
        - setype
                The type part of the SELinux filesystem object context.
                When set to `_default', it will use the `type' portion of the policy if available.
                default: null
                type: str
        
        - seuser
                The user part of the SELinux filesystem object context.
                By default it uses the `system' policy, where applicable.
                When set to `_default', it will use the `user' portion of the policy if available.
                default: null
                type: str
        
        - src
                Local path to a file to copy to the remote server.
                This can be absolute or relative.
                If path is a directory, it is copied recursively. In this case, if path ends with "/", only inside contents of that directory are copied to destination. Otherwise,
                if it does not end with "/", the directory itself with all contents is copied. This behavior is similar to the `rsync' command line tool.
                default: null
                type: path
        
        - unsafe_writes
                Influence when to use atomic operation to prevent data corruption or inconsistent reads from the target filesystem object.
                By default this module uses atomic operations to prevent data corruption or inconsistent reads from the target filesystem objects, but sometimes systems are
                configured or just broken in ways that prevent this. One example is docker mounted filesystem objects, which cannot be updated atomically from inside the container
                and can only be written in an unsafe manner.
                This option allows Ansible to fall back to unsafe methods of updating filesystem objects when atomic operations fail (however, it doesn't force Ansible to perform
                unsafe writes).
                IMPORTANT! Unsafe writes are subject to race conditions and can lead to data corruption.
                default: false
                type: bool
                added in: version 2.2 of ansible-core
        
        
        - validate
                The validation command to run before copying the updated file into the final destination.
                A temporary file path is used to validate, passed in through '%s' which must be present as in the examples below.
                Also, the command is passed securely so shell features such as expansion and pipes will not work.
                For an example on how to handle more complex validation than what this option provides, see handling complex validation.
                default: null
                type: str
        
        
        ATTRIBUTES:
        
                action:
                  description: Indicates this has a corresponding action plugin so some parts of the
                    options can be executed on the controller
                  support: full
                async:
                  description: Supports being used with the `async' keyword
                  support: none
                bypass_host_loop:
                  description:
        ...skipping...
        
        - md5sum
                MD5 checksum of the file after running copy.
                returned: when supported
                sample: 2a5aeecc61dc98c4d780b14b330e3282
                type: str
        
        - mode
                Permissions of the target, after execution.
                returned: success
                sample: '0644'
                type: str
        
        - owner
                Owner of the file, after execution.
                returned: success
                sample: httpd
                type: str
        
        - size
                Size of the target, after execution.
                returned: success
                sample: 1220
                type: int
        
        - src
                Source file used for the copy on the target machine.
                returned: changed
                sample: /home/httpd/.ansible/tmp/ansible-tmp-1423796390.97-147729857856000/source
                type: str
        
        - state
                State of the target, after execution.
                returned: success
                sample: file
                type: str
        
        - uid
                Owner id of the file, after execution.
                returned: success
                sample: 100
                type: int
        ...skipping...
        
        - md5sum
                MD5 checksum of the file after running copy.
                returned: when supported
                sample: 2a5aeecc61dc98c4d780b14b330e3282
                type: str
        
        - mode
                Permissions of the target, after execution.
                returned: success
                sample: '0644'
                type: str
        
        - owner
                Owner of the file, after execution.
                returned: success
                sample: httpd
                type: str
        
        - size
                Size of the target, after execution.
                returned: success
                sample: 1220
                type: int
        
        - src
                Source file used for the copy on the target machine.
                returned: changed
                sample: /home/httpd/.ansible/tmp/ansible-tmp-1423796390.97-147729857856000/source
                type: str
        
        - state
                State of the target, after execution.
                returned: success
                sample: file
                type: str
        
        - uid
                Owner id of the file, after execution.
                returned: success
                sample: 100
                type: int
 


---




