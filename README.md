# Droid Module: mysql

Install MySQL Server. For more information on Droid, please see
[droidphp.com](http://droidphp.com).

The steps involved are:-

1. Prevent the mysql-server package from interactively asking for a new root
   password.
2. Install mysql-server (and php5-mysql) packages.


## Assumptions

1. The platform is Debian-based.
2. The MySQL Service is not already installed.


## Limitations

1. The user-supplied root password is used for all MySQL services installed by
   this module.


## Information required by the module

1. One or more Inventory Hosts, having a `public_ip`.
2. Password values for the following variables:-

    mysql_root_password: <string>  # For the root user


## Optional information

1. An array of user accounts to create, with grants/permissions:

    mysql_users:
      -
        username: "repln"
        password: "super_secret_password_one"
        allowed-host: all
        grant: "REPLICATION SLAVE"
        grant-level: "*.*"
      -
        username: "joe"
        password: "super_secret_password_two"
        allowed-host: all
        grant: "SELECT, UPDATE, INSERT, DELETE, CREATE, INDEX, ALTER, DROP, LOCK TABLES, CREATE VIEW"
        grant-level: "*.*"
