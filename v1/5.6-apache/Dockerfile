# Drupal Commerce Docker Container
FROM mglaman/drupal-commerce:base-5.6-apache
MAINTAINER Matt Glaman <nmd.matt@gmail.com>

# Install Drupal via  drupal-composer/drupal-project
RUN composer create-project  drupal-composer/drupal-project \
 --stability dev \
 --no-interaction \
 .

# Require Drupal Commerce
RUN composer require drupal/commerce:7.1.*