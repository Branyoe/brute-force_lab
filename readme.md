# Brute force laboratory

## Description

This repository replicates a controlled environment where a brute force attack is practiced on a vulnerable server. Docker was used to facilitate the distribution of the project.

## Architecture

![Arch brute-forze lab - Página 1](https://github.com/Branyoe/brute-force_lab/assets/65278575/e5c96b9e-7c53-4e1f-b46f-88370817533c)


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
   ![image](https://github.com/Branyoe/brute-force_lab/assets/65278575/6987885b-6eb1-4ec7-b15e-5a7cc04079e5)

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
   ![image](https://github.com/Branyoe/brute-force_lab/assets/65278575/aecb23e3-e0b8-40e8-8fa7-7ae5cacc2f14)

8. espected result.
   ![image](https://github.com/Branyoe/brute-force_lab/assets/65278575/3a5cd9e9-8285-43ab-a030-e859adb6e6d9)

