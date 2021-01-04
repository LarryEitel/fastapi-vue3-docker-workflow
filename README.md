# fastapi-vue3-docker-workflow
Stubbing out and documenting FastAPI, VueJS 3 and Docker workflow.

![Build Containers for Prod & Push to Dockerhub](https://github.com/LarryEitel/fastapi-vue3-docker-workflow/workflows/Build%20Containers%20for%20Prod%20&%20Push%20to%20Dockerhub/badge.svg)


## Punchlist
- [x] Create sample vue frontend
  - From frontend DIR, [Vue CLI create project](https://cli.vuejs.org/guide/creating-a-project.html#vue-create) (Installed in same DIR and selected default Vue3)
  - yarn serve and [http://localhost:8080/](http://localhost:8080/)
- [X] Push to Git
- [X] Create Dockerfile to run Vue from Docker
  - From frontend DIR, [create Docker image](https://cli.vuejs.org/guide/deployment.html#docker-nginx)
  - docker build . -t frontend
  - docker run -d -p 8080:80 frontend
- [x] Create GitAction to build docker image and push to dockerhub
  - Confirm image arrived at private [hub.docker.com](https://hub.docker.com/)
- [x] Create [DigitalOcean](digitalocean.com) Droplet for <domain.com>
- [x] Setup Shell access
  - ([nice instructions](https://youtu.be/hf8wUUrGCgU?list=PLFBirL3MAv29JsC0G3ARt0fNWoK2PAdI6&t=205))
  - use puttygen to convert private key to <privateKey>.ppk
- [ ] Create user
- [ ] Install nginx
- [ ] Generate SSL


![Miro](images/MiroWorkFlow.png)


Inspired by [Deploying a Web App with Docker & Github Actions](https://www.youtube.com/watch?v=JsOoUrII3EY&list=PLFBirL3MAv29JsC0G3ARt0fNWoK2PAdI6&index=1)
