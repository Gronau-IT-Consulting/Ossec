##Installing the OSSEC agent on Proteus

The following process outlines how to install an OSSEC agent on Proteus.

Remove existing OSSEC artifacts:
```
sudo rm -f /etc/init.d/ossec /etc/rc0.d/K20ossec /etc/rc1.d/K20ossec /etc/rc2.d/S20ossec /etc/rc3.d/S20ossec /etc/rc4.d/S20ossec /etc/rc5.d/S20ossec /etc/rc6.d/K20ossec; sudo rm -rf /var/ossec; sudo /usr/sbin/deluser ossec; sudo /usr/sbin/deluser ossecm; sudo /usr/sbin/deluser ossecr; sudo /usr/sbin/deluser ossecd; sudo /usr/sbin/delgroup ossec; sudo /usr/sbin/delgroup ossecd
```
Add repo and install agent
```
sudo apt-key adv --fetch-keys http://ossec.wazuh.com/repos/apt/conf/ossec-key.gpg.key
sudo echo 'deb http://ossec.wazuh.com/repos/apt/ubuntu trusty main' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ossec-hids-agent
```
During the install, add the IP address of the Capricorn server.

![ossec_agent_1](https://cloud.githubusercontent.com/assets/16313160/18657954/39abbeee-7f42-11e6-85d6-14a696c0de2f.png)

Follow the SIEMonster Build Guide - https://siemonster.com/wp-content/uploads/2016/08/Kustodian-SIEMonster-Guide-V2.5.pdf Ch. 7.3 to install a new agent on Capricorn.

Run the following command on Proteus, choose 'I' and paste the key assigned for Proteus.

```
sudo /var/ossec/bin/manage_agents
```
![ossec_agent_2](https://cloud.githubusercontent.com/assets/16313160/18657955/39abdb86-7f42-11e6-8065-1b75bfb0588a.png)

Restart the OSSEC agent

```
sudo /var/ossec/bin/ossec-control restart
```

Expect some action on Capricorn.

