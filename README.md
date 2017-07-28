Walkthrough: Scaffolding plugin tests and trying execute unit test.

### Up Wordpress and MySQL containers.

    docker-compose up -d

### Install WordPress

    dc exec wordpress wp core install --allow-root --url=http://www.example.com/ --title=testing --admin_user=wpadmin --admin_email=wpadmin@example.com

### Scaffolding

    dc exec wordpress wp scaffold plugin-tests unittest-sample --allow-root

### Create empty plugin file

    echo "<?php" > unittest-sample.php

### Setup test environment.

    dc exec wordpress bash -c "/var/www/html/wp-content/plugins/unittest-sample/bin/install-wp-tests.sh wordpress_test root 'devpass' db latest"

### Try execute PHPUnit.

    dc exec wordpress bash -c "cd /var/www/html/wp-content/plugins/unittest-sample; phpunit"

