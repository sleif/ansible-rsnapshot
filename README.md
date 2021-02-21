sleif.rsnapshot
============

This role installs and configures rsnapshot sources and target.
It maintains /etc/rsnapshot.conf, rsnapshot root directory creation and ssh key management for remote targets.

Requirements
------------

n/a

Role Variables
--------------

rsnapshot_snapshot_root: /.snapshots

See in defaults/main.yml for common rsnapshot options.

Dependencies
------------

n/a

Example Playbook
----------------

    - hosts: "servers"
      roles:
        - { role: sleif.rsnapshot, tags: "rsnapshot",
            rsnapshot_backup_points: [
              { backup_host: "external-host", dir: "/etc/", target_dir: "external-hosts/", options: "one_fs=1,exclude=OlD/",
                                                            proxyjump: "jumphost.example.com", proxyjump_target: "192.168.12.34" },
              { backup_host: "", dir: "/srv/",   target_dir: "localhost/",
                                                            options: "one_fs=1, exclude=dir1/subdir1/, exclude=dir2/subdir2/",
                                                            proxyjump: "", proxyjump_target: "" }
              ]}
License
-------

MIT

Author Information
------------------

Created in 2021 by Sebastian Berthold
