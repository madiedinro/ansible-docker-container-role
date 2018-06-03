# Asible role for deploy service in docker container

Created for Ubuntu

## Usage

Add to ansible playbook following:

    - import_role:
        name: dr.docker-container
      vars:
        # [git repo with images]
        drdc_repo: '{{def_api_repo}}'
        # container name
        drdc_name: '{{def_api_service}}'
        # [dir for build/dir with sources]
        drdc_dir: '{{image souce directory}}'
        # [dir mode]
        drdc_dir_mode: 0755
        # [name for pull or name for build]
        drdc_image: "drdc/{{drdc_name}}-image"
        # [net to attach]
        drdc_network: '{{def_docker_net_name}}'
        drdc_env: '{{def_env|combine({"KEY": "value"})}}'
        drdc_volumes:
          - /data:/data:ro
        drdc_ports:
          - "8080:9000"
        # allocate a pseudo-TTY
        drdc_tty: no
        # keep stdin open after a container is launched
        drdc_interactive: no
      tags: ['container']


About ports, envs, volumes
http://docs.ansible.com/ansible/latest/modules/docker_container_module.html

## Default parameters

Discover in `defaults/main.yml`

## Requirements

Installed docker
