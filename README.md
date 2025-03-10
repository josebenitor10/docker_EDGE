# EDGE Container in Compose file.

## Intention

 To publish an automated solution to use EDGE fast. People that used this does not know how to set it up.
 Typing commands is error prone.


## Where to get it?
It is a Docker container. The portal explain several items, other you have to search for them.

https://hub.docker.com/r/bioedge/edge_24_ubuntu


## How to

1. Install docker or podman, not discussed here.
2. Play a little with the command. Do the training

https://docs.docker.com/compose/gettingstarted/

3. Download the compose.yaml file provided here.
4. Update volumen per your config taking into consideration provided information in the portal:

https://hub.docker.com/r/bioedge/edge_24_ubuntu

5. Add nginx as a proxy with certs.
Not  discussed here, may be added later.

6. Some default options should be audited, but you decide.
seccom:unconfined for example.


The volumens are directories share between the container and the host.

volumes:
  # Specify an absolute path mapping
  # - /optdatabase/EDGE_database:/home/edge/databse
  - /opt/database:/home/edge/database
  - /opt/database/EDGE_mysql:/var/lib/mysql  # DB will run in the host but executed in the container.
  - /opt/data/EDGE_output:/home/edge/edge_dev/edge_ui/EDGE_output
  - /opt/data/EDGE_input:/home/edge/edge_dev/edge_ui/EDGE_input
  - /opt/data/EDGE_report:/home/edge/edge_dev/edge_ui/EDGE_report
  - /opt/data/docker_edge_compose_dir/backups:/home/edge/backups  # To create mysqldumps
  - /opt/data/EDGE_input/public/data/pdd:/home/edge/edge_dev/edge_ui/EDGE_in
