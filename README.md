Walkthrough: Scaffolding plugin tests and trying execute unit test.

### Up Wordpress and MySQL containers.

    docker-compose up -d

### Install WordPress

    docker-compose exec wordpress wp core install --allow-root --url=http://www.example.com/ --title=testing --admin_user=wpadmin --admin_email=wpadmin@example.com

### Scaffolding

    docker-compose exec wordpress wp scaffold plugin-tests my-plugin --allow-root

### Create empty plugin file

    echo "<?php" > my-plugin.php

### Setup test environment.

    docker-compose exec wordpress bash -c "/var/www/html/wp-content/plugins/my-plugin/bin/install-wp-tests.sh wordpress_test root 'devpass' db latest"

### Try execute PHPUnit.

    docker-compose exec wordpress bash -c "cd /var/www/html/wp-content/plugins/my-plugin; phpunit"

