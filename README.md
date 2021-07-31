# ELK-Stack-Project-I

Tanveer Khan 04/03/2021 SMU Cybersecurity Boot Camp

This is a collection of Linux scripts and Ansible scripts from my Cybersecurity Bootcamp class.

The scripts are used to configure cloud servers with different docker containers.

The final setup was 4 servers running vulnerable DVWA containers along with a JumpBox and a server running an ELK Stack container.

![image](https://user-images.githubusercontent.com/74847116/127726650-730e7627-7b1e-4340-b4b7-44b6b8a1a9ea.png)

These files have been tested and are now being used to create a live ELK deployment on Azure. They may be used to re-create the whole deployment seen in the image above. Select components of the playbook (.yml) file, such as Filebeat, can also be used to install only certain parts of it.

The following ansible-playbooks are needed to create and install DVWA and the ELK-server:

![image]C:\Users\tanve\Documents\GitHub\ELK-Stack-Project\Resources\my-playbook.yml

![image]C:\Users\tanve\Documents\GitHub\ELK-Stack-Project\Resources\elk-playbook.yml

![image]C:\Users\tanve\Documents\GitHub\ELK-Stack-Project\Resources\filebeat.playbook.yml
