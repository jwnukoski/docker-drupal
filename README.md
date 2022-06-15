# What is this?
- This a Docker template for spinning up a development Drupal instance with a PHP / NGINX / MYSQL stack.  
- This project DOES NOT control your file permissions. You should follow best practices as needed. See the Drupal and SQL documentation.  
  
## Prior to running:  
1. Setup your Drupal files in 'src' directory. This should be a composer project with the 'web' directory. Refer to Drupal's official documentation on how to do this. From this directory, it would currently be:  
`composer create-project drupal/recommended-project src`  
  
2. Copy the example_docker-compose.yml to docker-compose.yml    
  
3. Modify the MYSQL_USER, MYSQL_PASSWORD, and MYSQL_DATABASE options in docker-compose.yml as needed.  
  
3. Modify your src/web/sites/default/settings.php to reflect the credentials in step 3. 'Host' should be set to 'db'.  
  
4. Run: docker compose up  
  
## Upgrading:  
- Modify PHP version in the ./php-fpm/Dockerfile. Update the tag in the line starting with 'FROM'. The Docker image should be FPM based.  
  
- Modify NGINX and MYSQL versions in the ./docker-compose.yml  
  
## Where are my files?: 
- SQL data is stored in the ./sql-data directory.  
  
- Drupal files should go in the ./src directory.  
  
- NGINX config is in the ./nginx directory.  

- Put your SSL certs in .nginx/certs. The will be mounted to /etc/nginx/certs. Update the file name in ./nginx/nginx.conf in ssl_certfiticate and ssl_certificate_key. Make sure to prepend your file paths with 'certs/'.

## Notes:  
- Never commit actual database credentials to the docker-compose.yml file. By default this file is in the .gitignore directory to prevent you from doing this.  
  
- This project is NOT intended to be used for production. Modify it at your own risk and needs.  
  
- For development ONLY, if you get file permission errors, you can do `chmod 777 -R ./src` for the fastest start. For HTTPS, you can also generate a self-signed cert like so:  
openssl req -newkey rsa:2048 -new -nodes -x509 -days 3650 -keyout key.pem -out cert.pem