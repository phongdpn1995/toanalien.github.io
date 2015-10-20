---
title: 403 Forbidden after changing DocumentRoot directory Apache
layout: post
---

I had the exact same problem and I solved it like this:

First; I followed the steps as explained on the Ubuntu Server Guide Pages

Go to terminal and copy the default virtual host configuration to a new one 

```bash
$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/mynewsite.conf
```

Edit this new file 

```text
sudo gedit /etc/apache2/sites-available/mynewsite.conf
```
and change the DocumentRoot to your own (save and close..)

Enable this new configuration file `sudo a2ensite mynewsite.conf` and dissable the default one `sudo a2dissite 000-default.conf`
Edit the apache2.conf `sudo gedit /etc/apache2/apache2.conf` and change the default -section into this: 

```text
<Directory [write_your_dir_here]>
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
</Directory>
```

Restart Apache2 `sudo service apache2 restart`

If it already works: great!