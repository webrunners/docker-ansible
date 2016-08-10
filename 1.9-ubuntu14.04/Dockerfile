FROM ubuntu:14.04

RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive \
    apt-get install --no-install-recommends -y -q \
            build-essential \
            python-pip python-dev python-yaml \
            libxml2-dev libxslt1-dev zlib1g-dev libffi-dev libssl-dev \
            ssh rsync unzip keychain && \
    pip install --upgrade pyyaml jinja2 pycrypto && \
    pip install --upgrade ansible==1.9.4 markupsafe && \
    apt-get remove -y --auto-remove \
            build-essential python-pip python-dev && \
    apt-get clean -y && \
    rm -r /var/lib/apt/lists/*
    # /var/cache/apt/archives/*

COPY splash /usr/local/bin/
COPY ssh_config /root/.ssh/config
RUN chmod a+x /usr/local/bin/splash && \
    echo 'eval `keychain --agents ssh --eval id_rsa`' >> ~/.bashrc


CMD [ "ansible-playbook", "--version" ]
