# Brute force laboratory

## Description

This repository replicates a controlled environment where a brute force attack is practiced on a vulnerable server. Docker was used to facilitate the distribution of the project.

## Architecture

...

## Usage

1. clone repo.

   ```bash
   git@github.com:Branyoe/brute-force_lab.git
   ```
2. run compose app.

   ```bash
   docker compose up -d
   ```
3. paste your dictionary.txt file in the dictionaries directory.
4. watch attacked container logs.

   ```bash
   docker logs attacked -f
   ```
5. in another console instance, inspect docker compose network to see attacked container IP.

   ```bash
   docker network inspect brute-force_lab_default
   ```
   ...
6. in another console instance, access to attacker container console.

   ```bash
   docker exec -it attacker /bin/bash
   ```
7. run attack.

   ```bash
   hydra \
   -l <target_user> \
   -P /dictionaries/<dictionary_name>.txt \
   <target_ip> -s <target_port> \
   http-form-post \
   "/<target_endpoint>:<body_req_user_key>=<target_user>&<body_req_password_key>=^PASS^:<successfully_msg>"
   ```
   ...
8. espected result.
   ...
