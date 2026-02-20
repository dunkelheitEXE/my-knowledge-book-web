---
{"dg-publish":true,"permalink":"/using-uncomplicated-firewall-ufw/","tags":["network"]}
---

## Installation

### Debian based systems

```shell
sudo apt install ufw
```

## Commands

### Basic commands

- `sudo ufw status`: This commands shows the firewall status, if it is enabled or not. If it is enabled, it will show you all active rules.
- `sudo ufw reset`: It deletes all rules created.
- `ufw enable`: It enables the firewall rules.
- `ufw disable`: It disables the firewall rules.
- `ufw status numbered`: It show the status of the firewall but with each rule numbered.
- `ufw delete ...`: This command deletes a rule from Firewall, in `...` must be the number of the index showed in `status numbered`
- `ufw reload`: In case that you change rules, this will reload all rules.
- `ufw default deny incoming`: It denies all incoming traffic.
- `ufw default deny outgoing`: It denies all outgoing traffic.
- `ufw app list`: This shows some applications that could need a firewall rule activated, instead of using the port of one of these, you can simply input the name of some app that you need using the command `ufw allow`.

### Some port rules

#### Traffic commands

- `ufw allow out ...`: This command will allow an outgoing rule.
- `ufw allow in ...`: This command will allow an incoming rile.

In `...` must be one of the next rules. These rules are related to the ports of your machine (ports that could manage the traffic with web pages, for example, the https and http, both allow rendering web pages on your browser)

#### Ports

**Rules for internet**

| Port | Port Name |
| ---- | --------- |
| 443  | https     |
| 80   | http      |
| 53   | dns       |

#### Output

Here I will explain some outputs which probably you will see at the moment you execute `ufw`

```text
Rule added # This means that a ipv4 rule has been added
Rule added (v6) # This means that a ipv6 rule has been added
```

>[!QUOTE] **References**