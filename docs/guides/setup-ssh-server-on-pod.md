# Setup SSH Server on Pod

Clone a public Template like Ubuntu 22.04 and modify the docker options to include -p 22:22 to expose port 22 to the internet.

Connect to the pod using webssh

run the following commands

apt update

apt install openssh-server vim

cd /etc/ssh

vi sshd\_config

uncomment the lines

\#PermitRootLogin prohibit-password

\#PasswordAuthentication yes

save the file with Esc followed by :wq!

restart sshd with&#x20;

service ssh restart

go to /root/.ssh

and paste the contents of your public\_key in file authorized\_keys

chmod 600 authorized\_keys



connect using default key file

ssh -p EXPOSED\_PORT ubuntu@POD\_PUBLIC\_IP

replace EXPOSED\_PORT with the port mapping for 22 port and use the POD\_PUBLIC\_IP from connect popup

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

e.g. ssh -p 41752 ubuntu@136.61.33.107



if your key is not in the default loation you can specify the key using -i

e.g.&#x20;

ssh -p 41752 ubuntu@136.61.33.107 -i key.pem
