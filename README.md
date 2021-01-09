# fastapi-vue3-docker-workflow
Stubbing out and documenting FastAPI, VueJS 3 and Docker workflow.

NOTE: This is a sandbox project. Glean ideas only.


![Build Containers for Prod & Push to Dockerhub](https://github.com/LarryEitel/fastapi-vue3-docker-workflow/workflows/Build%20Containers%20for%20Prod%20&%20Push%20to%20Dockerhub/badge.svg)

## Must Reads
- [x] [Deploying Self-Hosted Github Actions Runners with Docker](https://testdriven.io/blog/github-actions-docker/)


## Punchlist
- [x] Create sample vue frontend
  - From frontend DIR, [Vue CLI create project](https://cli.vuejs.org/guide/creating-a-project.html#vue-create) (Installed in same DIR and selected default Vue3)
  - yarn serve and [http://localhost:8080/](http://localhost:8080/)
- [X] Push to Git
- [X] Create Dockerfile to run Vue from Docker
  - [Dockerizing a Vue App](https://mherman.org/blog/dockerizing-a-vue-app/)
    
  - For Dev
    - docker build -f ./frontend/DockerfileDev -t frontend:dev ./frontend
    - Hot loading doesn't work with this as expected. Only with docker-compose
    - docker run -it -v ${PWD}:/app -v /app/node_modules -p 8080:8080 -e CHOKIDAR_USEPOLLING=true --rm frontend:dev
    - docker-compose -f docker-compose-dev.yml up -d

  - For Prod
    - docker build -f ./frontend/Dockerfile -t frontend:prod ./frontend
    - winpty docker run -it -p 80:80 --rm frontend:prod
    - docker-compose
    - docker-compose up -d --build
    

- [x] Create GitAction to build docker image and push to dockerhub
  - Confirm image arrived at private [hub.docker.com](https://hub.docker.com/)
- [x] Create [DigitalOcean](digitalocean.com) Droplet for <domain.com>
- [x] Setup Shell access
  - ([nice instructions](https://youtu.be/hf8wUUrGCgU?list=PLFBirL3MAv29JsC0G3ARt0fNWoK2PAdI6&t=205))
  - use [puttygen](https://www.ssh.com/ssh/putty/windows/puttygen) to convert private key to <privateKey>.ppk
- [x] Replace ubuntu prompt
  - PS1=$
- [ ] Create user
  - adduser larry
  - adduser larry sudo
    - or usermod -aG sudo larry?
  - sudo su - larry
  - verify docker group exists
    - cat /etc/group
  - as root: add user to docker group
    - sudo usermod -aG docker larry
- [ ] Github runner
  - Nice
    - [Automatically Deploy Docker + Wordpress To Digitalocean With Github Actions - CI&CD](https://youtu.be/-nT1Xs7-qqA?t=1225)
    - [Deploying Self-hosted Runners for GitHub Actions](https://www.youtube.com/watch?v=G6nBM3NxBDc)
    - [Deploying to Digitalocean](https://stackabuse.com/deploying-a-node-js-app-to-a-digitalocean-droplet-with-docker/)
  - [github actions](https://github.com/LarryEitel/fastapi-vue3-docker-workflow/settings/actions)
    - [See final part of comment re deploy image to DO](https://www.digitalocean.com/community/questions/automatic-deployment-using-github-actions-digital-ocean-registry-into-a-droplet)
    - Add runner following instructions
    - Install as service
      - from /home/larry/actions-runner
        - sudo ./svc.sh install
        - sudo ./svc.sh start
        - sudo ./svc.sh status
- [x] Docker Prep
  - mkdir /root/devops
  - cd /root/devops
  - docker login
  - pull image
    - docker pull larryeitel/fastapi-vue3-docker-workflow
  - run container and verify
    - docker run -d -p 8080:80 larryeitel/fastapi-vue3-docker-workflow
    - [http://<dropletIP>:8080/](http://<dropletIP>:8080/)
- [ ] [Install nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04)
  - sudo apt update
  - sudo apt install nginx
  - ufw allow 'Nginx HTTP'
  - ufw delete allow 'Nginx HTTP'
  - Confirm server is running
    - systemctl status nginx
  - Key nginx commands
    - sudo systemctl stop nginx
    - systemctl start nginx
    - systemctl restart nginx
    - sudo systemctl reload nginx
    - systemctl disable nginx
    - systemctl enable nginx
    - systemctl status nginx.service
  - Visit droplet IP to see NGINX page.
  - Configure nginx
    - ln -s /etc/nginx/sites-available/<domain> /etc/nginx/sites-enabled/<domain>
  - Update snap
      - snap install core; sudo snap refresh core
  - snap install --classic certbot


- [X] Generate SSL
  - Check ubuntu version: cat /etc/os-release
  - Visit [Certbot](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04)
  - certbot --nginx -d example.com -d www.example.com
  - Verify `systemctl status certbot.timer`



![Miro](images/MiroWorkFlow.png)


Inspired by [Deploying a Web App with Docker & Github Actions](https://www.youtube.com/watch?v=JsOoUrII3EY&list=PLFBirL3MAv29JsC0G3ARt0fNWoK2PAdI6&index=1)
