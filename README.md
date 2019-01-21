This vagrant file deploys 5 machines
-
  - 3 CentOS-7 machines
    - manager
    - web1
    - web2
    
  - 2 Ubuntu-16.04 machines
    - db1
    - db2


manager server
   
    - manager.example.com 
      IP: 172.16.1.100
      OS: Centos 7

web servers

    - web1.example.com
      172.16.1.201
      OS: Centos 7

    - web2.example.com
      172.16.1.202
      OS: Centos 7

db servers

    - db1.example.com
      172.16.1.203
      OS:

    - db2.example.com
      172.16.1.204
      OS: Ubuntu 16.04
