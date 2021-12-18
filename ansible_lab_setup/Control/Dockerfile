FROM ubuntu_base:latest

# install ansible package
RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
    ansible

# copy content of ansible directory from local disk to file system inside Docker image
COPY ansible /var/ansible/

# change working directory
WORKDIR /var/ansible

# generate RSA key pair to allow master to communicate with managed nodes
# default private key passphrase is '12345' (this passphrase should not be used on prod)
RUN ssh-keygen -t rsa -N 12345 -C "master key" -f master_key
