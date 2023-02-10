dnf-automatic
=========
This role can be used to schedule dnf-automatic notifyonly timer as well as dnf-automatic install timer. Clients will auto-apply available patches at the scheduled time which we need to provide as a variable.

Usage
------------
#ansible-playbook playbook.yml -i inventory.ini

Requirements
------------
The client should have postfix configured (postfix will be installed in case not installed already) to send mail notifications to users. Client should also have registered to entitlement server to download patches from.

Role Variables
--------------
Following variables to be added in inventory file.
[patch]
hostname1
hostname2

[patch:vars]
#OnCalendar Event for NotifyOnly timer,to be added in  YYYY-MM-DD HH:MM format
Notify_Timer= Thu,Fri *-*-* 12:00:00

#Comma seperated email addresses to send notifications to.
mailing_list= 

#Randomized delay variable. (default 60m if not defined)
RandomDelay= 15m

#OnCalendar Event for Installing patches,to be added in YYYY-MM-DD HH:MM format
Update_Timer= 2023-02-09 12:30:00

#State of the dnf-automatic-install.timer service, options are started,restarted,stopped. Default is stopped
service_state= started


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

---
- name: Default playbook
  hosts: all
  become: true
  roles:
  - role: dnf-automatic
    tags: dnf

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
