# eng_poc
Proof of Concept for ENG classes

## Pre-requisites
- macosx or linux with tmux installed (windows, please use ubuntu vagrant box)
- docker and docker-compose installed
  - vm.max_map_count=262144
  - linux sysctl -w vm.max_map_count=262144
 - macos https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-prod-mode

## Instructions
- clone the repository
- cd eng_poc
- run docker-compose -p lab up -d
- **important don't forget -p lab in the previous line**
- chmod +x es3k1
- ./es3k1
- to switch between the windows use Ctrl-a n 
