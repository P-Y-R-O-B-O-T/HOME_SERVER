# HOME_SERVER

![](ZZZ/ZZZ.jpg)

🏡 Welcome to My Home Server Oasis! 🚀

Dive into my DIY setup powered by Ansible and Docker:

📊 Grafana: Real-time system monitoring made easy.
🎬 Jellyfin: Your ticket to seamless streaming.
🚫 Pi-hole: Say goodbye to annoying ads! Host your own DNS!
📁 File Browser: Effortless file management and media browsing.

Join me in unleashing the full potential of our digital haven! 💻✨

## PREREQUISITE
* Have keys for accessing your server via ssh.
* Have ansible installed on your local system.

## INSTALLATION
* Clone this repo on you local system
```
git clone https://github.com/P-Y-R-O-B-O-T/HOME_SERVER.git && cd HOME_SERVER
```

* Change the IP in `ANSIBLE/INVENTORY/home_server.yaml` to your server's `IP` or `HOST_NAME`.

* Run all these commands below with replacing `SERVER_USERNAME` by your server's username and then input `server's user's PASSWORD`

* Enable firewall.
```
ansible-playbook -i ANSIBLE/INVENTORY/home_server.yaml ANSIBLE/PLAYBOOKS/enable_firewall.yaml -u SERVER_USERNAME -kK
```

* Install dependencies
```
ansible-playbook -i ANSIBLE/INVENTORY/home_server.yaml ANSIBLE/PLAYBOOKS/install_docker_dependencies.yaml -u SERVER_USERNAME -kK
```

* Create directory structures
```
ansible-playbook -i ANSIBLE/INVENTORY/home_server.yaml ANSIBLE/PLAYBOOKS/create_directories.yaml -u SERVER_USERNAME -kK
```

* Generate self signed certificates
```
ansible-playbook -i ANSIBLE/INVENTORY/home_server.yaml ANSIBLE/PLAYBOOKS/generate_certificates_self_signed.yaml -u SERVER_USERNAME -kK
```

## FINAL DEPLOYMENT STEP
* SSH into your server and run the following commands
```
cd HOME_SERVER
```
```
sudo docker compose up -d --force-recreate
```

* VOILLA, YOUR SERVER IS RUNNING

## USAGE
* Goto these urls to access services

* Grafana
```
https://SERVER_HOSTNAME:11111
```

* Jellyfin
```
https://SERVER_HOSTNAME:11112
```

* Pi Hole
```
https://SERVER_HOSTNAME:11113
```

* File Browser
```
https://SERVER_HOSTNAME:11114
```

## ADVANCED USAGE
* By default we cant upload files to jellyfin using Web `WEB UI`.

* Here we have very good solution to that thing

* All movies will be in the base path specified.

* Upload files to /movies directory using `File Browser`.

* Click scan all albums in jellyfin dashboard.

* You are good to go. New movies are here !!
