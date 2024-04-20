# HOME_SERVER

![](ZZZ/ZZZ.jpg)

# **Intuitive Home Server Setup with Raspberry Pi 🌐🏠**

Welcome to the future of home computing! 🚀 Ready to transform your Raspberry Pi into a powerful home server? Let's get started!

### Are you ready to elevate your home network? 🛠️💾

1. **Hardware Setup**: Got your Raspberry Pi, power supply, and microSD card ready to go?
   
2. **Software Installation**: Ready to flash the latest Raspberry Pi OS onto your microSD card?

3. **Network Integration**: Are you prepared to connect your Raspberry Pi to your home network for seamless data transfer?

4. **Enhanced Security**: Ready to fortify your digital fortress with advanced encryption and authentication?

### Are you excited about the features? 🛡️💾

- **Advanced File Sharing**: Share files effortlessly across devices within your home network.
   
- **Immersive Media Streaming**: Dive into a world of entertainment with smooth media streaming capabilities.
   
- **Secure Remote Access**: Access your home server securely from anywhere in the world.

### How will you use your home server? 📲💻

Access its features from any device within your home network and enjoy seamless connectivity.

### What future enhancements are you looking forward to? 🚀🔮

Stay tuned for updates and enhancements to your home server experience.

### Need support along the way? 🛠️👩🚀

Our support team is here to help! Contact us at this repo's issue section for expert guidance.

## 🏡 Welcome to My Home Server Oasis! 🚀
### Dive into my DIY setup powered by Ansible and Docker:

1. 📊 **Grafana**: Real-time system monitoring made easy. Keep an eye on performance metrics like CPU usage and network activity, whether you're using a Raspberry Pi or an old laptop!

2. 🎬 **Jellyfin**: Your ticket to seamless streaming. Turn your Raspberry Pi or spare PC into a media powerhouse, streaming your favorite movies and TV shows effortlessly.

3. 🚫 **Pi-hole**: Say goodbye to annoying ads! 🛡️ Whether you've got a Raspberry Pi lying around or an old PC, transform it into an ad-blocking DNS server and enjoy a cleaner browsing experience.

4. 📁 **File Browser**: Effortless file management and media browsing. Got files to share or a media library to organize? Utilize your Raspberry Pi or old laptop as a file server and enjoy hassle-free file management.

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

# License 📜🔒

This project is licensed under the MIT License. See the LICENSE file for more information.
