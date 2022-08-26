sudo
=========

Role to managed sudoers files in /etc/sudoers.d.  Basically this role will setup different sudoers files and options based on the value passed into the sudoer templates.

Requirements
------------

N/A

Role Variables
--------------

Variables that can be used to create different sudoers:

{{ sudoers }} - dictionary that contain the following
  {{ username }} - free text, which provide the username to be insert into either "sudo.j2" or "sudo_nopasswd.j2"
  {{ sudo_user }} - boolean value.  If "yes", the it will use "sudo.j2"
  {{ sudo_user_nopasswd }} - boolean value.  If "yes", the it will use "sudo_nopasswd.j2"
  {{ custom_sudoers }} - free text, which allow you to setup customized sudo command for the user


Templates for creating different sudoers:
sudo.j2 - basic sudo to all with password require
sudo_nopasswd.j2 - basic sudo to all without password require
custom_user_sudo.j2 - customized sudoer with diff commands


Dependencies
------------

N/A

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: sudo, x: 42 }

License
-------

CC BY-NC 2.0

Author Information
------------------

