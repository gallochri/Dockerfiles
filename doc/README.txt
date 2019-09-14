1. Build Images
    $ docker build -t gallochri/galera:0.0.1 .

2. Run Container
    $ docker run -p 3306:3306 --name gall0 gallochri/galera:0.0.1

3. Run Container and open a shell
    $ docker run --name gall0 -it gallochri/galera:0.0.1 /bin/bash

3. Open shell in running container
    $ docker exec -it gal0 /bin/bash


4. Cleaning
    $ docker system prune -f          # will remove all stopped containers, all dangling images, and all unused networks
    $ docker rmi gallochri/galera:0.0.1 # will delete image