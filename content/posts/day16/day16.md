---
title: "Day 16"
date: 2021-06-16T22:20:32+05:30
---

First I corrected the asciinema problem in the previous post.

I then managed to build a simple nginx docker build at the port 8080.

![Nginx site built using Docker.](/posts/day16/img/site_docker_nginx.PNG)

I did this by following [this tutorial in YouTube](https://www.youtube.com/watch?v=kkazBPHc4bk).

[![asciicast](https://asciinema.org/a/UxA50TJpkymBvcXhwtcVERUSK.svg)](https://asciinema.org/a/UxA50TJpkymBvcXhwtcVERUSK)

I then attempted to follow [this tutorial](https://www.bogotobogo.com/DevOps/Ansible/Ansible-Deploy-Nginx-to-Docker.php) to help understand the process behind Ansible and Docker.

```
root@aarabdh-VirtualBox:/home/k/.ssh# adduser k sudo
Adding user `k' to group `sudo' ...
Adding user k to group sudo
Done.
root@aarabdh-VirtualBox:/home/k/.ssh# sudo visudo
```

I added the new user, got the IP address, did the ssh thing, but then I encountered this error:

```
ssh: connect to host 172.17.0.x port 22: Connection refused
```

{{< highlight terminal >}}
aarabdh@aarabdh-VirtualBox:~/ansible_docker$ ssh k@172.17.0.2
ssh: connect to host 172.17.0.2 port 22: Connection refused
{{< /highlight >}}

I searched Google, and found some links like [Ask Ubuntu](https://askubuntu.com/questions/144364/ssh-connect-to-host-myremotehost-com-port-22-connection-refused) and [Stack Overflow](https://stackoverflow.com/questions/17335728/connect-to-host-localhost-port-22-connection-refused)

I tried restarting the ssh service, re-insalling it, but all to no avail.