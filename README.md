devbox
======

This role sets up my shell environment the way I like it.

Requirements
------------

Export the token from Github for adding SSH public key;

    export GITHUB_TOKEN='abc123'

You might need to change some defaults (e.g. when on cygwin) in `ansible.cfg`:

    [defaults]
    host_key_checking = False
    remote_user = ubuntu
    private_key_file = ~/.ssh/ansible-monport
    deprecation_warnings = False

    [ssh_connection]
    control_path = /tmp
    ssh_args = -o ControlMaster=no
    pipelining = True

Example Playbook
----------------

    - hosts: gandalf.reisingers.org
      become: True

      vars:
        os_user: jreisinger
        github_token: "{{ lookup('env','GITHUB_TOKEN') }}"

      roles:
        - { role: devbox }
