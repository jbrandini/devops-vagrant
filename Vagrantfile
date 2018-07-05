# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: <<-SHELL
    mkdir /root/.ssh/
    echo "127.0.0.1 localhost
192.168.99.10 docker.salas4linux.com.br
192.168.99.11 devops.salas4linux.com.br
192.168.99.12 automation.salas4linux.com.br" > /etc/hosts
    #CHAVE PRIVADA
    echo "-----BEGIN RSA PRIVATE KEY-----
MIIEpgIBAAKCAQEA3axFtJr+G7+o4WxqkBv1odZzdis/rJxZ3NhE+9KG3ClO/lA7
stYrbzalM7c7U8FPB/cgmXW/SytWfschKOhtSV3rYgkwFSZLC0A8kZ4MjZ0H5ddO
bQFrPpJ+zDn9qmgH0A+0kreTW6ZWeE10gIzvDqBK+G6LS8tJLOUJQjLuI0ifRd2W
13/ryahGncwN8FgiPWqIKRu4FegyX7oY2nHD01dg7tcPDcoYcKGmgI4NVdf7VCLp
NeqRNQ5ZK2b+1Hmff0G2zZeRmSO6VumLnnPIEiCPcVz6sZrmNIRXbgZbnS+Nb/hX
0Wt0Q6zzB/EwW3YiURoCn2OcLm/hTqd9JlZNzwIDAQABAoIBAQCSJ2WGILLuBL4K
cvsHrQeU/tn9zaIb4rJ1I7rH9hSo0CufDbNuxDq7BuKBaIwbOtcqv0ulIrdPjnFn
AU/hsu1rdBsf9kLXjvnnnyDQOc65CBIO/phc0pStGtWzPYD8e7669b/vBE6KHO/i
Pd9UaperoxALIIeDH7NNgG1MUlwksiDJFwES7Zpd2YyA+g+p7kRC8wiGySjbKrKW
nFEUWQxe1kDqYyS/mVM/tDXq1Pe4Ctz0PcmHgn9A44PnzQm2SrzOhY03qxVkwDno
5xuJq4XRE+1n+nwQ/gtTlVjb0ce/w8mRMWTBGUBC7COMmy3qQB02Y4BU2JOMT3uL
unTLbxNxAoGBAPctUrQH02r6XsyfZZJoGPsWT9q10CdGQMjYgma0JSHsY/z8Bpii
5r16LCszFAcP0YAI3+YcRg+wrnV3xZ2harqCSL6Z981JzHLvNUWcqQ4NR3QvEBCf
1GvcvHBSUJpAtHH+FBPDNx/fOSkccdMEKVfyGO8xUh3rRGiq7l5exGNdAoGBAOWV
5T8Ok6XdeI0LQ94U0CY7sLbM5mZsyaJHFbbotPivimWdjDqKIj7Qo8dC179o7ema
R3Ht1hcFXAKVonwKqXKf/Y6DITxarsrjUeZJCMiQ6vviExEUbckSEY3gpnXuua+x
9EAneoD9zRSx+kW3nwbJZ6xOGxzDPZ/7tu/YjO8bAoGBANz60SiQoovOoLgxfR5i
IItCDExNJXYnUb3+Cr8FKPlmHJJNQxxs7vrQ4fIRLUOO+c6MoJdaCaz3WVE9rhfZ
+tAZsC1u+2K2KqlKgIbmoyEj8BDIDoW+TqvL4VBN1y/Az1HmRE7SxVKiP7koa/6q
hsfQckhOAMsszbEBuC/4a30lAoGBAL1qPCcYKayw2mLTpny1gz3oBVXsGzLqEjk2
mK29tIFwoqhPoYAysypMDLO7bDDZq2AOD1/pr7Zyj4T6W4InccHGSfWoLmWTE58E
iW+LVhnTpmuGC+ENj75Sj/UUIYIvITfZhADiEWoW+3pVlHyskCGTTVuVXT0Pv+oc
TMP5T919AoGBAPaSILh9/U6QuvIAIduTruFnJBQPMSI/XmjrecgdHNWo27hYurpY
mZAAdNfs7FLd3MmwDJR0fwtCgjiR/ksTCvZzn3Lxsv0FH9S4Zpe0O5HH+PPpHiLy
BWBLxrRobBQN7B41Lr9wNbbltW2QbZgvGLagIe3WWxWJ7dI+i9mQGoP8
-----END RSA PRIVATE KEY-----" > /root/.ssh/id_rsa
    #CHAVE PUBLICA
    echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDdrEW0mv4bv6jhbGqQG/Wh1nN2Kz+snFnc2ET70obcKU7+UDuy1itvNqUztztTwU8H9yCZdb9LK1Z+xyEo6G1JXetiCTAVJksLQDyRngyNnQfl105tAWs+kn7MOf2qaAfQD7SSt5NbplZ4TXSAjO8OoEr4botLy0ks5QlCMu4jSJ9F3ZbXf+vJqEadzA3wWCI9aogpG7gV6DJfuhjaccPTV2Du1w8NyhhwoaaAjg1V1/tUIuk16pE1DlkrZv7UeZ9/QbbNl5GZI7pW6Yuec8gSII9xXPqxmuY0hFduBludL41v+FfRa3RDrPMH8TBbdiJRGgKfY5wub+FOp30mVk3P" > /root/.ssh/authorized_keys
    chmod 600 /root/.ssh/id_rsa
  SHELL

#DOCKER
  config.vm.define "docker" do |docker|
    docker.vm.hostname = "docker"
    docker.vm.box = "ubuntu/xenial64"
    docker.vm.box_check_update = false
    docker.vm.network "private_network", ip: "192.168.99.10", dns: "8.8.8.8"
  end

#DEVOPS
  config.vm.define "devops" do |devops|
    devops.vm.hostname = "devops"
    devops.vm.box = "ubuntu/xenial64"
    devops.vm.box_check_update = false
    devops.vm.network "private_network", ip: "192.168.99.11", dns: "8.8.8.8"
    config.vm.provider "virtualbox" do |devops|
      devops.memory = "3072"
    end
  end

#AUTOMATION
  config.vm.define "automation" do |automation|
    automation.vm.hostname = "automation"
    automation.vm.box = "centos/7"
    automation.vm.box_check_update = false
    automation.vm.network "private_network", ip: "192.168.99.12", dns: "8.8.8.8"
    end

  end
