# ansible-adhoc

ansible all -i "10.0.1.15," -m raw -a "ls -la" --user ubuntu --private-key ~/.ssh/xxxx-nodes-kp.pem

-s -- runs command as sudo 

ansible spark-cluster -i hosts -s -m raw -a "test -e /usr/bin/python || (apt-get -y update && apt-get install -y python3 python-simplejson)"

-b -- runs command as sudo ( become )

ansible spark-cluster -i hosts -b -m raw -a "test -e /usr/bin/python || (apt-get -y update && apt-get install -y python3 python-simplejson)"

###### create group

ansible all -i hosts -b -m group -a "name=hadoop state=present"

###### create user

ansible all -i hosts -b -m user -a "name=spark shell=/bin/bash groups=hadoop append=yes"

ansible all -i hosts -b -m file -a "path=/usr/dap state=directory owner=spark group=hadoop mode=0775"
