## prep

    echo $VAULT_PASS > vault_pass.txt  # Get VAULT_PASS

### using ansible within docker

    alias manage='docker-compose run --rm nucleus'  # bash
    doskey manage='docker-compose run --rm nucleus'  # cmd

### using ansible locally

    alias manage='ansible-playbook --vault-password-file vault_pass.txt -i'  # bash

## run

    manage env/dev run/provision.yml
    manage env/dev run/deploy.yml

## raw

    docker-compose run --rm nucleus
    docker-compose up --build  # Rebuild after changing Dockerfile
    
    docker-compose run --rm nucleus env/dev run/provision.yml
    docker-compose run --rm nucleus env/dev run/deploy.yml
    docker-compose run --rm --entrypoint="ansible -i" nucleus env/dev -m ping all

    ansible-playbook --vault-password-file vault_pass.txt -i env/dev run/provision.yml
    ansible-playbook --vault-password-file vault_pass.txt -i env/dev run/deploy.yml
    ansible -m ping -i env/dev all
    
## update passwords
    
    ansible-vault encrypt passwords.yml
    ansible-vault edit passwords.yml
    ansible-vault rekey passwords.yml  # Change password
    ansible-vault decrypt passwords.yml  # Do not commit unencrypted!
