#  10.1 «Keepalived/vrrp» -Семериков Алексей
# Код первой ноды

```MarkDown
vrrp_instance test {

state MASTER

interface enp0s3

virtual_router_id 10

priority 110

advert_int 5

authentication {

auth_type AH

auth_pass 12345

}

unicast_peer {

192.168.0.140

}

virtual_ipaddress {

192.168.0.90 dev enp0s3 label enp0s3:vip

}

}

```

# код второй ноды 

```MarkDown
vrrp_instance test {

state BACKUP

interface enp0s3

virtual_router_id 10

priority 90

advert_int 5

authentication {

auth_type AH

auth_pass 12345

}

unicast_peer {

192.168.0.170

}

virtual_ipaddress {

192.168.0.90 dev enp0s3 label enp0s3:vip

}

}

```

![сотояние master ноды](https://github.com/olimp85/keepalived/blob/main/MASTER%20State.bmp)
![состояние backup ноды](https://github.com/olimp85/keepalived/blob/main/BACKUP%20State.bmp)

