City-of-Bloomington.apache
=========

Install Apache along with common packages on Ubuntu using apt.

Requirements
------------

City-of-Bloomington.linux

Example Playbook
----------------
```yml
- hosts: linux-apache
  become: yes
  roles:
    - City-of-Bloomington.linux
    - City-of-Bloomington.apache
```

Copying and License
-------
This material is copyright 2016 City of Bloomington, Indiana
It is open and licensed under the GNU General Public License (GLP) v3.0 whose full text may be found at:
https://www.gnu.org/licenses/gpl.txt
