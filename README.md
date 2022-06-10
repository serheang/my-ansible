# my-ansible
Welcome to my ansible playbooks!

This is just some of the playbooks I had wrote for myself, or for the works I did.
I tried to make sure the playbooks is generic and flexible for the general public to use/reuse/refer/modify, but there could be some mistakes/assumptions that you might want to check/verify before using them.

My standard layout of my ansible follow the Ansible Best Practice here http://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#directory-layout, with some simplication to suit my needs:


    production                # inventory file for production servers
    staging                   # inventory file for staging environment

    group_vars/ 
       all                    # here we assign variables to particular groups
       group2                 # ""
    host_vars/
       localhost              # if systems need specific variables, put them here
       hostname2              # ""

    site.yml                  # master playbook
    vmplayer.yml              # playbook for installing vmware player
    gnome.yml                 # playbook for setting gnome 

    roles/
        common/               # this hierarchy represents a "role"
            tasks/            #
                main.yml      #  <-- tasks file can include smaller files if warranted
            handlers/         #
                main.yml      #  <-- handlers file
            templates/        #  <-- files for use with the template resource
                ntp.conf.j2   #  <------- templates end in .j2
            files/            #
                bar.txt       #  <-- files for use with the copy resource
                foo.sh        #  <-- script files for use with the script resource
            vars/             #
                main.yml      #  <-- variables associated with this role
            defaults/         #
                main.yml      #  <-- default lower priority variables for this role
            
        webtier/              # same kind of structure as "common" was above, done for the webtier role
        monitoring/           # ""
    playbooks/                # adhoc playbooks
    
