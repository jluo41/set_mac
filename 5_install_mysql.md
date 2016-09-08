## 5. Install MySQL

#### 5.1 Use DMG
Even we can install MySQL with the command `"$ brew install mysql"`, but there are much troubles to deal before get the MySQL to work.

So using DMG to install MySQL is first recommended.

1. Download DMG for MySQL website: http://dev.mysql.com/downloads/mysql/

  Open this web page, and scroll the bottom, find the file ended with `.dmg`, and download it.

2. Open it and install

  Just follow the instruction.

  ![The password](http://ww3.sinaimg.cn/mw690/005WT5Wygw1f7mjezi048j30bx069q3z.jpg)

  But be __cautious__: after all files installed, MySQL will pop a small window with a temporary password. Keep that password, otherwise you will
  in endless troubles.

3. Configure MySQL

   You still need to do something before MySQL can actually run.

   ![Preference Settings](http://ww4.sinaimg.cn/mw690/005WT5Wygw1f7mjexc81sj30ii0ggacu.jpg)

   First, start MySQL server, open your System Preferences, in its bottom you will say an icon with the name: MySQL.
   click it and then start your server.

   Second, export mysql's PATH.

   In your root directory, open the file named `.bash_profile` [ or `.zshrc` if you have replace `bash` with `zsh`],

   add this line then save it.

   `export PATH="/usr/local/mysql/bin:$PATH"`

4. Change password

  On the terminal, enter:

  `mysql -u root -p`

  Then you are asked to enter password. The password should be the one that MySQL gave you after installation, and you should __store__ it already,
  find it and enter. Then you will enter `mysql` mode.

  Change the password, by entering:

  `SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpass');`

  With a frequently used new password, please.

5. Set MySQL configuration file

    The default MySQL file is in `/etc/my.cnf`. We still need to add some configuration variables to handle with the encoding problem, that is, to set 'utf-8' as defaults.

    But you should create one. There is no such file originally.

    `$ sudo touch /etc/my.cnf`

    Then open it with your text editor, such as atom.

    Add the following lines into the file.

    ```
    [client]
    default-character-set = utf8

    [mysqld]
    default-storage-engine = INNODB
    character-set-server = utf8
    collation-server = utf8_general_ci
    ```

    Then MySQL can come to work.

#### 5.2 Use `brew`

1. Install mysql by:

  `brew install mysql`

2. Set mysql user and database directory

  ```
  $ unset TMPDIR
  $ mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp
  ```

3. Automatically Start MySQL on Startup

  ```
  $ mkdir -p ~/Library/LaunchAgents

  $ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents

  $ find /usr/local/Cellar/mysql/ -name "homebrew.mxcl.mysql.plist" -exec cp {} ~/Library/LaunchAgents/ \;
  $ launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
  ```

4. Set `my.cnf`

  Make a `my.cnf` by:

  `sudo touch my.cnf`

  Add the content in the following template to '/etc/my.cnf' and save it.


```
# /etc/my.cfn
#
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with
# ticks/quotes escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing
# the socket location.
[client]
port        = 3306
#socket     = /var/run/mysqld/mysqld.sock

default-character-set = utf8

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions
# are currently parsed.
[mysqld_safe]
#socket     = /var/run/mysqld/mysqld.sock
#nice       = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses
#   apparmor, you may also need to also adjust
#   /etc/apparmor.d/usr.sbin.mysqld.
#


default-storage-engine = INNODB
character-set-server = utf8
collation-server = utf8_general_ci

#user       = mysql
#socket     = /var/run/mysqld/mysqld.sock
port        = 3306
#basedir    = /usr
datadir    = /usr/local/var/mysql
#tmpdir     = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer          = 16M
max_allowed_packet  = 16M
thread_stack        = 192K
thread_cache_size   = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections       = 100
#table_cache           = 64
#thread_concurrency    = 10
#
# * Query Cache Configuration
#
query_cache_limit   = 1M
query_cache_size    = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /usr/local/var/mysql/MacBook15.local.err

# Here you can see queries with especially long duration
#log_slow_queries   = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or
# for replication.
# note: if you are setting up a replication slave, see
#       README.Debian about other settings you may need
#       to change.
#server-id          = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size     = 100M
#binlog_do_db       = include_database_name
#binlog_ignore_db   = include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem

# Query Caching
query-cache-type = 1

# Default to InnoDB
default-storage-engine=innodb

[mysqldump]
quick
quote-names
max_allowed_packet  = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer      = 16M
```
