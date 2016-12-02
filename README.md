## prep

    echo $VAULT_PASS > vault_pass.txt  # Get VAULT_PASS
    mv .env.example .env  # Edit for not using ssh-agent

### using ansible within docker

    alias manage='docker-compose run --rm ansible ansible-playbook --vault-password-file vault_pass.txt -i'  # bash
    doskey manage='docker-compose run --rm ansible ansible-playbook --vault-password-file vault_pass.txt -i'  # cmd

### using ansible locally

    alias manage='ansible-playbook --vault-password-file vault_pass.txt -i'  # bash

## run

    manage env/dev run/provision.yml
    manage env/dev run/deploy.yml
