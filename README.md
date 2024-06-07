
# Display Wildfires on Map with Flask 


1. Install Docker from https://www.docker.com/products/docker-desktop/
2. Run commands in terminal to set up and install postgis and Docker containers   
    >docker network create postgresnet

    >docker run -d --name postgis --network=”postgresnet” -e POSTGRES_PASSWORD=wfpass -e POSTGRES_DB=wildfires -p 5432:5432 postgis/postgis

    >docker run -d -p 8080:80 --network=”postgresnet” -e PGADMIN_DEFAULT_EMAIL=admin@gmail.com -e PGADMIN_DEFAULT_PASSWORD=pgadmin_password dpage/pgadmin4


![postGIS](https://github.com/daniel2036/disProject/assets/71909361/343c9617-592c-48e5-80a4-17e85e3fbd75)
