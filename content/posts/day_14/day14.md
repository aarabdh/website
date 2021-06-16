---
title: "Day 14"
date: 2021-06-14T10:10:09+05:30
---

#### Ansible

Today I got introduced to Ansible, that is useful for deploying instrucions to many different systems using a really simple "YAML" format.    
I watched its intro video, then tried to follow a tutorial to learn the initial setup needed. I installed it successfully but was faced with an error.

I added this to my hosts file:

```
[ansible_client]
192.168.56.1 ansible_ssh_user=root ansible_ssh_pass=(Redacted)
```

And also wrote up this YAML file:

{{< highlight yaml >}}
---
- name: sample book
  hosts: ansible_client
  remote_user: root
  become: true
  tasks:
    - name: install httpd
      yum:
          name: httpd
          state: latest
    - name: run httpd
      service:
              name: httpd
              state: started
    - name: create content
      copy:
           content: "Congrats on installing ansible"
           dest: /var/www/html/index.html
{{< /highlight >}}

But I kept encountering this error: 

```
[Warning]: Could not match supplied host pattern, ignoring: ansible_client
```

The error was resolved, it was a simple typing error on my part in the hosts file.