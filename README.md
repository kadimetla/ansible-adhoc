# ansible-adhoc

ansible all -i "10.0.1.15," -m raw -a "ls -la" --user ubuntu --private-key ~/.ssh/xxxx-nodes-kp.pem

ansible spark-cluster -i hosts -s -m raw -a "test -e /usr/bin/python || (apt-get -y update && apt-get install -y python3 python-simplejson)"
