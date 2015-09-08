# Rails, PostgreSQL with Passenger + Nginx on Ubuntu 14.04 without RVM or rbenv

* https://www.brightbox.com/docs/ruby/ubuntu/
* https://www.phusionpassenger.com/library/install/nginx/install/oss/trusty/
* http://www.postgresql.org/download/linux/ubuntu/
* https://github.com/rvm/rvm/blob/493b5bdcec50a2b521a6cad307334a3a4425099f/scripts/functions/requirements/ubuntu#L124

1. `ssh-copy-id -i ~/.ssh/id_rsa.pub root@SERVER`
2. `scp rails-passenger-postgres-nginx root@SERVER:/root/rails-passenger-postgres-nginx`
3. `ssh root@SERVER "./rails-passenger-postgres-nginx app_name db_pass"`

If you have error `No PostgreSQL clusters exist` you should configure locale:

in /etc/default/locale:

    LANG=en_US.UTF-8
    LANGUAGE=en_US.UTF-8
    LC_ALL=en_US.UTF-8
    LC_CTYPE=en_US.UTF-8

run `dpkg-reconfigure locales` and after `pg_createcluster 9.4 main --start`
