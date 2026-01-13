---
{"dg-publish":true,"permalink":"/introduction-to-postgre-sql/","tags":["DataBases"]}
---

## Introduction

>PostgreSQL is a powerful, open source object-relational database system that uses and extends the SQL language combined with many features that safely store and scale the most complicated data workloads.
>
>📎 [PostgreSQL Official Documentation](https://www.postgresql.org/about/)

> Unlike other RDBMSs (relational database management systems), PostgreSQL supports both relational and non-relational data types. This makes it one of the most compatible, stable, and mature relational databases available today.
> 
> 📎 [IMB. What is PostgreSQL](https://www.ibm.com/mx-es/think/topics/postgresql)

## First Steps

### Installation

To install PostgreSQL in a Linux-based system, you can download via official repositories (in case of Debian-based distributions):

#### Linux

##### Debian-Based Distributions

```shell
sudo apt install postgresql
```

### Start

Now, when you install for first time, postgresql creates a user named "*postgres*", so to start postgresql you have to type in terminal 

```shell
sudo -u postgres psql
```

Once you push `enter`, you will be seeing in your terminal the shell to use postgres:

![Pasted image 20260113121257.png](/img/user/Pasted%20image%2020260113121257.png)

### First commands

Some basic commands learning to use the postgres shell:

```text
# This command allows you to see all databases stored in postgres
\l 

# To exit from postgres
\q
```

Using postgres by first time, you will be aware that `postgres` user does not have a password, so we have to set one:

>[!INFO] Important
>You have to follow the syntax exactly that here you can see. You must use `'` instead of `"`

```shell
alter user <user-name> with password 'new_password'

# To this example it will be
alter user postgres with password 'password'
```

Now you will be able to connect remotely using password

### Graphical Application

If you wish to use PostgreSQL using a graphical desktop application, you can install *pgadmin* via package:

#### Debian-based distributions

```shell
sudo apt-get install pgadmin
```

>[!QUOTE] **References**
>📎 [PostgreSQL Official Documentation](https://www.postgresql.org/about/)
>
>📎 [IMB. What is PostgreSQL](https://www.ibm.com/mx-es/think/topics/postgresql)

