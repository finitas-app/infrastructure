# Infrastructure

This repository contains scripts and structures that are important when running an entire system.
These include docker-compose, which builds a snapshot based on compiled code, docker-compose, which builds
a snapshot based on uncompiled files and does compilation at snapshot time, and kubernetes yaml.

## Requirements

First of all, you need to clone all the finitas-app organization repositories into one empty folder.
For example, if you created a finitas-app folder and cloned all repositories there, then after writing
the `ls` command you should see the following output(order is not important):
`finance-manager-store finitas-frontend-api finitas-mobile-app infrastructure receipt-processor room-manageer`

## Launching a compiled project

1. To compile the project, run the `build` file located in the root of the infrastructure directory. 
To compile successfully make sure you have java 17 installed and the environment variable JAVA_HOME set, 
you can check this by writing `echo $JAVA_HOME`, you should see the path to java.
If you fail to build the project, try doing it with Docker side build and run. This is described in the next heading.

2. You should find out your local ip address.Write the command `ifconfig`, in the case of Windows `ipconfig`, and find
an address starting with `192.168.`. Then go to the file docker-compose.yml located in the root directory of the infrastructure
project and replace the host on line 6 with your ip address. For example, if my address is `192.168.64.1`, the result should be `"192.168.64.1:8080:8080"`.
This is necessary to start the system that will have your ip address as host. This will give you the ability to make
requests not only from the local machine but also for example from your phone if you run a mobile application, but you must be connected to the same network. 
If you want to run the project locally and make requests only with a local http client, you can leave only `"8080:8080"`.

3. Write the command `docker compose up -d`

## Docker side build and run

1. Navigate to the `docker-side-build` directory.

2. You should find out your local ip address.Write the command `ifconfig`, in the case of Windows `ipconfig`, and find
   an address starting with `192.168.`. Then go to the file docker-compose.yml located in the root directory of the infrastructure
   project and replace the host on line 8 with your ip address. For example, if my address is `192.168.64.1`, the result should be `"192.168.64.1:8080:8080"`.
   This is necessary to start the system that will have your ip address as host. This will give you the ability to throw
   requests not only from the local machine but also for example from your phone if you run a mobile application.
   If you want to make requests only with a local http client, you can leave only `"8080:8080"`.

3. Write the command `docker compose up -d`
