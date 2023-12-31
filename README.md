# Setting up Neo4j with Docker

## Instructions

To set up Neo4j using Docker, follow these steps:

1. **Install Docker:**
   If you haven't already installed Docker, you can download it from [Docker's official website](https://www.docker.com/).

2. **Create a Docker Compose File:**
   Create a `docker-compose.yml` file in your project directory with the following content:

   ```yaml
   version: "3.8"
   services:
     neo4j:
       image: neo4j:latest
       ports:
         - 7888:7474
         - 7999:7687
       restart: unless-stopped
       environment:
         NEO4J_AUTH: neo4j/password
       volumes:
         - ./db/data:/data
         - ./db/logs:/logs
         - ./db/conf:/conf
         - ./db/plugins:/plugins
   ```

3. **Start Neo4j Container:**
   Open a terminal and navigate to the directory containing the `docker-compose.yml` file.
   Run the following command to start Neo4j:

   ```bash
   docker-compose up
   ```

4. **Wait for Neo4j to Start:**
   Allow some time for the Neo4j container to start. You can monitor the progress by checking the logs.

5. **Access Neo4j Desktop:**
   Once the container is running, open Neo4j Desktop.
   Click on "Add Graph" and select "Connect to Remote Graph."

6. **Enter Connection Details:**
   Enter the following details:

   - Host: localhost
   - Bolt Port: 7687 (or the port you specified in the `docker-compose.yml` file)
   - Username: neo4j
   - Password: password (replace with your desired password)

7. **Connect to Neo4j:**
   Click on "Connect" to establish a connection to the Neo4j database.

Now you are ready to use Neo4j with your application!

## Note

- Ensure to replace "password" with your desired password in both the `docker-compose.yml` file and the Neo4j Desktop connection details.
- If you've changed the port mappings, update the Neo4j Desktop connection details accordingly.
