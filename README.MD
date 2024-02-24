1. shell script is homogeneous

2. one shell script can work only on one particular distribution, means your shell script may not work for all linux servers.

   example: useradd sriram for centos and adduser sriram for ubuntu.

3. For every step we need to do validations.

4. Suppose if we have 20 servers we have to login into 20 servers and run the script.

5. And it is imperative(little tough syntax) ---->imperative syntax focuses on detailing the steps to achieve a result, while 

   

Ansible:

1. Ansible can query the server and it can understand what os it is and based on that it can change the command.

2. No need to write validations for each and every step.

3. It can connect to any no of servers and executes the task without login into each and every server.

4. Declarative: syntax describes what result is desired without specifying the exact steps to achieve it.

Ansible works as a push mechanism where ansible control server connects to the nodes and it pushes the configurations into the nodes and

runs the tasks.

---------------------------------------------------------------------------------------------------------

create 2 centos linux machines and make one machine as ansible manager server and other one as ansible managed node.

In the ansible manager server install ansible using --> yum install ansible.

ansible all -i 172.31.28.89, -e ansible_user=centos -e ansible_password=Devops321 -m ping ---> This command is used for pinging 

the ansible host from ansible manager server. In this command "all" means all hosts that Ansible knows about.

sshpass -p 'DevOps321' ssh centos@172.31.41.124 touch /tmp/test

ansible all -i 172.31.94.92,172.31.90.103 -m ping -e ansible_user=centos -e ansible_password=DevOps321 ---> This pings to two servers

ansible all -i inv -m ping -e ansible_user=centos -e ansible_password=DevOps321 --> Kept the two node ips's in a inventory file called 

inv

ansible web -i inv  -m ping -e ansible_user=centos -e ansible_password=DevOps321 ---> Here in inventory we are pinging only the to 

group called web