# pg_bck_configfile

pg_bck_configfile is a bash script used to backup configuration files and versioning them through git.

Every time one or more files change, pg_bck_configfile make a new commit with current timestamp.

# Requirements

- git
- psql

# Examples

```bash
[mbona92@arch pg_bck_configfile]$ ./pg_bck_configfile --help
Usage:
   pg_bck_configfile [OPTION]

Options:
  -b, --bck-dir    where to backup config files
  -l               log directory

  --help           display this help

Database connection options:
  -d               connect to database name
  -h               database server host or socket directory
  -p               database server port number
  -U               connect as specified database user
  -P               if specified, prompt for postgres user's password

Server connection options:
  --host           server host to connect to copy config file
  --user           os user used to connect to server host

```

```bash
[mbona92@arch pg_bck_configfile]$ ./pg_bck_configfile -b /home/mbona92/config_file -l /home/mbona92/log -d postgres -h pghost -p 5432 -U postgres -P
Insert password for user postgres: 
[mbona92@arch pg_bck_configfile]$ 
[mbona92@arch pg_bck_configfile]$ ls -ltra /home/bona92/config_file
total 52
drwx--x---+ 44 mbona92 mbona92  4096 Oct 11 16:25 ..
-rw-------   1 mbona92 mbona92 23926 Oct 11 16:25 postgresql.conf
-rw-------   1 mbona92 mbona92  4723 Oct 11 16:25 pg_hba.conf
-rw-------   1 mbona92 mbona92  1636 Oct 11 16:25 pg_ident.conf
-rw-------   1 mbona92 mbona92    88 Oct 11 16:25 postgresql.auto.conf
drwxr-xr-x   3 mbona92 mbona92  4096 Oct 11 16:25 .
drwxr-xr-x   8 mbona92 mbona92  4096 Oct 11 16:25 .git

[mbona92@arch pg_bck_configfile]$ cd /home/mbona92/config_file
[mbona92@arch config_file]$ git log
commit af0b9f753023176284f938c9568b21a28bfe4111 (HEAD -> master)
Author: mbona92 <mbona92@gmail.com>
Date:   Fri Oct 11 16:25:59 2019 +0200

    Config file at 2019-10-11 16:25
```

