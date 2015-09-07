# Rails, PostgreSQL with Passenger + Nginx on Ubuntu 14.04 without RVM or rbenv

* https://www.brightbox.com/docs/ruby/ubuntu/
* https://www.phusionpassenger.com/library/install/nginx/install/oss/trusty/
* http://www.postgresql.org/download/linux/ubuntu/
* https://github.com/rvm/rvm/blob/493b5bdcec50a2b521a6cad307334a3a4425099f/scripts/functions/requirements/ubuntu#L124

        $ ssh-copy-id root@SERVER -i ~/.ssh/id_rsa.pub
        $ ssh root@SERVER
        # apt-get update && apt-get upgrade
        # ufw allow 22
        # ufw allow 80
        # ufw allow 443
        # ufw enable
        # sed -i '/PasswordAuthentication yes/PasswordAuthentication no' /etc/ssh/sshd_config
        # service ssh restart
        # apt-get --yes install software-properties-common apt-transport-https ca-certificates
        # apt-add-repository ppa:brightbox/ruby-ng
        # echo deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main > /etc/apt/sources.list.d/pgdg.list
        # echo deb https://oss-binaries.phusionpassenger.com/apt/passenger trusty main > /etc/apt/sources.list.d/passenger.list
        # wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
            sudo apt-key add -
        # apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 561F9B9CAC40B2F7
        # apt-get update
        # apt-get install -y ruby2.2 ruby2.2-dev make patch nginx-extras passenger postgresql-server-dev-9.4 postgresql-9.4
        # echo 'gem: --no-document' > /etc/gemrc
        # gem install rails pg
        # sudo -u postgres template1
        template1=# CREATE USER app_name WITH PASSWORD 'myPassword';
        template1=# CREATE DATABASE app_name;
        template1=# GRANT ALL PRIVILEGES ON DATABASE app_name to app_name;
        # adduser --disabled-password --gecos "" user
        # mkdir /home/user/.ssh
        # cp ~/.ssh/authorized_keys /home/user/.ssh
        # chown -R user:user /home/user/.ssh
        # echo 'user ALL=(ALL) NOPASSWD: bundle' >> /etc/sudoers
