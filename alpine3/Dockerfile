FROM williamyeh/ansible:alpine3-onbuild

RUN adduser -u 1000 -D -h /home/webrunners -g "" -s /bin/false webrunners
RUN apk --update add \
 rsync \
 openssh-client

USER webrunners
RUN mkdir -p /home/webrunners/app
WORKDIR /home/webrunners/app

ENTRYPOINT [ "ansible-playbook", "--vault-password-file", "vault_pass.txt", "-i" ]

CMD [ "env/dev", "--list-hosts", "run/provision.yml" ]
