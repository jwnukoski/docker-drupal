# What is this?
- This a Docker template for spinning up Drupal instance with a PHP / NGINX / MYSQL stack.  
- This project DOES NOT control your file permissions. You should follow best practices as needed. See the Drupal and SQL documentation.  
- This project doesn't currently set up SSL for you.
## Prior to running:  
1. Setup your Drupal files in 'src' directory. This should be a composer project with the 'web' directory.  
2. Modify the MYSQL_USER, MYSQL_PASSWORD, and MYSQL_DATABASE options in docker-compose.yml as needed.  
3. Modify your src/web/sites/default/settings.php to reflect the credentials in step 2.
## To run:  
docker compose up  

## Upgrading:  
- Modify PHP version in the ./php-fpm/Dockerfile. Update the tag in the line starting with 'FROM'. The Docker image should be FPM based.  
- Modify NGINX and MYSQL versions in the ./docker-compose.yml

## Where are my files?: 
- SQL data is stored in the ./sql-data directory.  
- Drupal files should go in the ./src directory.  
- NGINX config is in the ./nginx directory.  

## Notes:  
- Never commit actual database password to the docker-compose.yml file. By defaul this file is in the .gitignore directory to prevent you from doing this.