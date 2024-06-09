
# Display Wildfires on Map with Flask 
![postGIS](https://github.com/daniel2036/disProject/assets/71909361/343c9617-592c-48e5-80a4-17e85e3fbd75)

1. Download project repository zip from Github, unzip and open folder on VS Code
2. Install Docker from https://www.docker.com/products/docker-desktop/
3. Run commands in terminal to set up and install postgis and Docker containers   
    >docker network create postgresnet

    >docker run -d --name postgis --network=”postgresnet” -e POSTGRES_PASSWORD=wfpass -e POSTGRES_DB=wildfires -p 5432:5432 postgis/postgis

    >docker run -d -p 8080:80 --network=”postgresnet” -e PGADMIN_DEFAULT_EMAIL=admin@gmail.com -e PGADMIN_DEFAULT_PASSWORD=pgadmin_password dpage/pgadmin4

4. Start Docker Containers like this:
![docker_Container](https://github.com/daniel2036/disProject/assets/71909361/f0dbafb0-bb36-428c-800a-105ce369c38c)

5. Once the Docker containers started, log in http://localhost:8080/browser/ with email admin@gmail.com and password pgadmin_password to use pgadmin4 and manage database.
6. From pgadmin4 on localhost:8080
   
    ![gis1](https://github.com/daniel2036/disProject/assets/71909361/892fe354-240d-40de-bdb9-229fee291e5f)
    ![gis2](https://github.com/daniel2036/disProject/assets/71909361/017006b9-ddde-4ce0-b038-eaf0d750cf6a)

   (password in Connection should be wfpass) then save
7. Run all the cells in inserting_data.ipynb on VS Code to import wildfires.csv data to pgadmin4
8. Make sure 'postgis' is in the wildfires extensions. If not, right click on Extensions and create 'postgis'

   ![image](https://github.com/daniel2036/disProject/assets/71909361/c4d6baa1-9188-43e4-a222-448b1bf63ad9)


9. Create a new Docker container for pg_tileserv. This will be used to populate the map with wildfire data by rendering a layer.

   >docker run --network="postgresnet" -dt -e DATABASE_URL=postgresql://postgres:wfpass@postgis/wildfires -p 7800:7800 pramsey/pg_tileserv:latest

   
   ![pg_tiles](https://github.com/daniel2036/disProject/assets/71909361/e86e13b0-2fe7-48ad-9311-6f48bca3c5ef)
