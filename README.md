Role Name
=========

[![Build Status](https://travis-ci.org/Blue-Bag/ansible-role-apache.svg?branch=master)](https://travis-ci.org/Blue-Bag/ansible-role-apache)

This role has taken from geerling guy and combined with BBApache setup

Differences to geerlingguy

- use a template for the ports.cnf
- other apache configs (fqdn)
- disabling mods

This role sets up a default vhost with several inclusions. It is part of the BB server build and may not suite your needs.
Unless you specificaly require the additions contaned here you would be better using the geerlinguy.apache role from Ansible galaxy

Full documentation of thsi role is yet to be done.




Role Variables
--------------
to_do

### Prefork MPM limits (Debian)

Set directives in `mods-available/mpm_prefork.conf`. Each key is a prefork directive; Apache is reloaded on change. The default (`{}`) leaves the file alone.

```
apache_mpm_prefork_settings:
  MaxRequestWorkers: 20
  MaxConnectionsPerChild: 1000
```

Size `MaxRequestWorkers` to the RAM left over after the other services, divided by the memory per Apache/mod_php process (around 100 MB for a Drupal or WordPress site). The Debian default of 150 can exhaust memory on a small server under a burst of requests.


Dependencies
------------



Notes:
-----------


When setting an alias - set any directory directives you need to apply - if they are not specified explicitly else where

e.g.

```
Alias /css /path/to/my/css
<Directory /path/to/my/css />
      AllowOverride None
      Options -Indexes +SymLinksIfOwnerMatch -MultiViews
</Directory>
```


Stapling for SSL
https://www.digitalocean.com/community/tutorials/how-to-configure-ocsp-stapling-on-apache-and-nginx

Apache session cache / reuse
http://serverfault.com/questions/400089/apache2-sslsessioncache-running-but-not-working

License
-------

BSD

Author Information
------------------
George Boobyer
