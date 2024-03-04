---
- name: Install nginx, mysql, php and display phpinfo()
  hosts: localhost
  gather_facts: false

  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present

    - name: Install mysql
      apt:
        name: mysql-server
        state: present

    - name: Install php
      apt:
        name: php
        state: present

    - name: Create phpinfo.php file
      copy:
        content: "<?php phpinfo(); ?>"
        dest: /var/www/html/phpinfo.php

    - name: Restart nginx
      service:
        name: nginx
        state: restarted
