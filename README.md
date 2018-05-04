# Asible role for deploy service in docker container

Created for Ubuntu

## Usage

Add to ansible playbook following:

    - import_role:
        name: dr.docker-container
        drdc_repo: https://github.com/....
        drdc_name: myservice
        drdc_dir: /home/user/service1
        drdc_volumes:
          - /data
        drdc_network: bridge
        drdc_ports:
          - "8080:9000"
        drdc_env: {}
        tags: ['docker']

additional (by default computed from main params):

        drdc_image: "drdc/{{drdc_name}}-image"


params:
- **drdc_repo:** (str) git repo to fetch image source
- **drdc_name:** (str) new container name
- **drdc_dir:** (str) dir that will be used for building
- [**drdc_volumes:**] (list) volumes list. syntax from ansible docker_container http://docs.ansible.com/ansible/latest/modules/docker_container_module.html
- [**drdc_network:**] (str) attach container to not default network
- [**drdc_ports:**] (list) port map
- [**drdc_env:**] (dict) key/values dict with env variables
- [**drdc_image:** (str)] name of image that will builded for new service

## Default parameters

Discover in `defaults/main.yml`

## Requirements

Installed docker