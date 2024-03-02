# Getting Started:

- Clone or download the repository containing the docker-compose.yml files.
- Open a terminal and navigate to the directory containing the `docker-compose.yml` file you want.

``Note``: you can change the `ports`, `networks` and `volumes` as you wish. 

## Start the database services:
```Bash
docker-compose up -d
```
This command will create and start all the services defined in the docker-compose.yml file in detached mode (`-d`).

## Environment Variables:

The `docker-compose.yml` file defines environment variables within itself to configure certain aspects of the database service (e.g., database name, username, password). You can customize these variables directly within the file.

### Modifying Environment Variables in docker-compose.yml:

- Open the docker-compose.yml file with a text editor. 
- Find the section defining environment variables for your database service.
- This section typically looks like the following:
```yaml
environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: dbname
      MYSQL_USER: dbuser
      MYSQL_PASSWORD: dbpassword
```
Here, you can modify the values after the equal sign (`=`) for each variable.
- For example, to change the database name to "new_database", edit the line to:
```yaml
    MYSQL_DATABASE: new_database
```
### Alternative: Using a `.env` File:

While modifying environment variables directly in the docker-compose.yml file allows for quick changes, it can be `less secure` and version control friendly.

As an alternative, you can create a `.env` file in the same directory as the `docker-compose.yml` file. This file should contain your desired environment variables in the format:
```
DATABASE_NAME=new_database
DATABASE_USER=my_user
DATABASE_PASSWORD=my_password
```
Modify the docker-compose.yml file by adding the following line under the service definition:
```yaml
environment:
  DATABASE_NAME: ${DATABASE_NAME}
  DATABASE_USER: ${DATABASE_USER}
  DATABASE_PASSWORD: ${DATABASE_PASSWORD}
```
This tells Docker Compose to read environment variables from the .env file, allowing you to manage them separately from the main configuration file.

## Important:

**Never commit the `.env`** file to version control as it may contain sensitive information like passwords.
Consider using a .env.example file to provide an example of the .env file structure and prevent accidental commits of the actual .env file.

## Stopping and Removing Services:
#### Stop all services:
```Bash
docker-compose down
```
#### Remove all containers, volumes, and networks:
```Bash
docker-compose down -v
```
## Additional Notes:

This script provides a basic overview of using the Docker Compose file. Refer to the official documentation for Docker and Docker Compose for more advanced usage and troubleshooting:
- Docker: [link](https://docs.docker.com/)
- Docker Compose: [link](https://docs.docker.com/compose/) <br/>
The specific configuration options available in the docker-compose.yml file will depend on the database and its setup. Consult the specific documentation for your chosen database for further configuration details.


