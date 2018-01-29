# Apigee Edge Drupal module

A Drupal 8 module that turns a site into a developer portal for Apigee's API management product.

# Installing

```sh
$ composer require drupal/apigee_edge
```

If you experience a conflict with `symfony/property-info`, you should try to update  the `phpdocumentor/reflection-docblock` library with `composer update phpdocumentor/reflection-docblock` because Drupal 8.4.x by default installs 2.0.4 (as a dependency of PHPUnit 4.8) and it is in conflict with one of Apigee Edge PHP SDK's required libraries (the above mentioned `symfony/property-info:^3.2`) minimum requirements.  

# Testing

To run the tests, some environment variables are needed both for the script and the server. These variables are:
* `APIGEE_EDGE_ENDPOINT`
* `APIGEE_EDGE_ORGANIZATION`
* `APIGEE_EDGE_USERNAME`
* `APIGEE_EDGE_PASSWORD`.

You can set these environment variables multiple ways, either by defining them with `export` or `set` in the terminal or creating a copy of the `core/phpunit.xml.dist` file as `core/phpunit.xml` and specifying them in that.

Run the following command to execute tests of this module (note that the location of the `phpunit` executable might be different in your case):

```sh
./vendor/bin/phpunit -c core --verbose --color --group apigee_edge
```

If you have Docker and Docker Compose installed on your system you can also run PHPUnit tests of this module with the following commands:

```sh
$ docker-compose -f docker-compose.yml -f docker-compose.apigee_edge.yml build php
$ docker-compose up -d
$ docker-compose -f docker-compose.yml -f docker-compose.apigee_edge.yml run php sh /opt/drupal-module/test.sh
```

You can read more about running Drupal 8 PHPUnit tests [here](https://www.drupal.org/docs/8/phpunit/running-phpunit-tests).
