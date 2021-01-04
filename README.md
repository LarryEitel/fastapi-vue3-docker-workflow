# fastapi-vue3-docker-workflow
Stubbing out and documenting FastAPI, VueJS 3 and Docker workflow.

## Punchlist
- [x] Create sample vue frontend
  - From frontend DIR, [Vue CLI create project](https://cli.vuejs.org/guide/creating-a-project.html#vue-create) (Installed in same DIR and selected default Vue3)
  - yarn serve and [http://localhost:8080/](http://localhost:8080/)
- [X] Push to Git
- [X] Create Dockerfile to run Vue from Docker
  - From frontend DIR, [create Docker image](https://cli.vuejs.org/guide/deployment.html#docker-nginx)
  - docker build . -t frontend
  - docker run -d -p 8080:80 frontend
- [ ] Create GitAction to build docker image and push to dockerhub
- [ ] Create DigitalOcean Droplet for craulio.com
- [ ] Setup Shell access
- [ ] Create user
- [ ] Install nginx
- [ ] Generate SSL


![Miro](images/MiroWorkFlow.png)


Inspired by [Deploying a Web App with Docker & Github Actions](https://www.youtube.com/watch?v=JsOoUrII3EY&list=PLFBirL3MAv29JsC0G3ARt0fNWoK2PAdI6&index=1)
