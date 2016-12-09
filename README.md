City-of-Bloomington.apache
=========

Maintains Apache along with common packages on Ubuntu using apt.

This role enables SSL for all web traffic, and redirects URLs from
port 80 to port 443.  If you do not specify SSL key and cert data,
then a self-signed cert will be generated.

Requirements
------------

City-of-Bloomington.linux

Role Variables
--------------

You must set variables for either a self-signed cert or provide your own,
preexisting key and cert data.

### Self Signed

```yml
apache_ssl:
  key:
    file: server.key
  cert:
    file: server.crt
    subj: /C=US/ST=Indiana/L=Bloomington/O=City of Bloomington/OU=ITS/CN={{ ansible_host }}
```

### Custom key and certificate

```yml
apache_ssl:
  key:
    file: custom.key
    data: |
      -----BEGIN RSA PRIVATE KEY-----
      ...
      -----END RSA PRIVATE KEY-----
  cert:
    file: thawte.crt
    data: |
      -----BEGIN CERTIFICATE-----
      ...
      -----END CERTIFICATE-----
```

You can also provide an intermediate certificate chain file

```yml
apache_ssl:
  key:
    file: custom.key
    data: |
      -----BEGIN RSA PRIVATE KEY-----
      ...
      -----END RSA PRIVATE KEY-----
  cert:
    file: thawte.crt
    data: |
      -----BEGIN CERTIFICATE-----
      ...
      -----END CERTIFICATE-----
  chain:
    file: intermediate.crt
    data: |
      -----BEGIN CERTIFICATE-----
      ...
      -----END CERTIFICATE-----
```

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
