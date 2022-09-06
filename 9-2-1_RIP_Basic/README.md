# 9-2-1_RIP_Basic

## RIPバージョンのデフォルト

ルーティング情報送信は2がデフォルト。受信は両方がデフォルト。

CISCOルータでは(たぶん送信も受信も)1がデフォルト。

9-2-1_RIP_BasicではEXOSのデフォルト設定を使う。

```
* sw1.7 # enable rip
* sw1.8 # enable rip export direct cost 1
* sw1.9 # configure rip add vlan Routing1
* sw1.10 # show config rip detail 
#
# Module rip configuration.
#
configure rip garbagetime 120
configure rip import-policy none
configure rip routetimeout 180
configure rip updatetime 30
disable rip originate-default
disable rip use-ip-router-alert
disable rip aggregation
enable rip poisonreverse
enable rip splithorizon
enable rip triggerupdates
enable rip
enable rip export direct cost 1 tag 0
disable rip export static 
disable rip export ospf-intra 
disable rip export ospf-inter 
disable rip export ospf-extern1 
disable rip export ospf-extern2 
disable rip export e-bgp 
disable rip export i-bgp 
disable rip export isis-level-1 
disable rip export isis-level-2 
disable rip export isis-level-1-external 
disable rip export isis-level-2-external 
configure rip add vlan Routing1
configure rip vlan Routing1 route-policy out none
configure rip vlan Routing1 route-policy in none
configure rip vlan Routing1 trusted-gateway none
configure rip vlan Routing1 rxmode any      ##### 受信
configure rip vlan Routing1 txmode v2only   ##### 送信
configure rip vlan Routing1 cost 1
* sw1.11 # 

```