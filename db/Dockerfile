FROM mysql
RUN mysql -u root -p drupal -e 'CREATE database drupal IF NOT EXISTS'
RUN mysql -u root -p drupal -e "GRANT ALL PRIVILEGES ON drupal. * TO 'drupal'@*'"
RUN mysql -u root -p drupal -e "FLUSH PRIVILEGES"