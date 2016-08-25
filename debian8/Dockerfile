FROM williamyeh/ansible:debian8

RUN adduser webrunners -u 1000 --disabled-password --home /home/webrunners --gecos "" --shell /bin/false
RUN apt-get update -q &&\
 apt-get dist-upgrade -y &&\
 apt-get install -yq --no-install-recommends apt-utils rsync less vim

USER webrunners
RUN mkdir -p /home/webrunners/app
WORKDIR /home/webrunners/app

ENTRYPOINT [ "ansible-playbook", "--vault-password-file", "vault_pass.txt", "-i" ]

CMD [ "env/dev", "--list-hosts", "run/provision.yml" ]
