```
docker system prune

# stop all containers:
alias dkillall='docker kill $(docker ps -q)'

# remove all containers
alias drmac='docker rm $(docker ps -a -q)'

# remove all images
alias drmai='docker rmi $(docker images -q)'

alias dcu='docker-compose up -d'



alias d='docker'
alias db='docker build'
alias dbsw='winpty docker run --rm -it --volumes-from sug-application sug-workspace bash'
alias dc='docker-compose'
alias dcb='docker-compose build'
alias dcl='docker-compose logs'
alias dcleandkx='dcleandkxfunction'
alias dcp='docker-compose ps'
alias dcpossh='winpty docker-compose exec -d php-fpm service ssh start'
alias dcs='docker-compose stop'
alias dcssh='docker-compose exec -d php-fpm service ssh start'
alias df='df -kTh'
alias di='docker images'
alias dk='docker'
alias dl='docker logs -f'
alias dm='docker-machine'
alias dp='docker ps'
alias dpa='docker ps -a'
alias dr='winpty docker run --rm -i -t'
alias drmf='docker rm -f $(docker ps -aq)'
alias drmv='docker volume rm $(docker volume ls | awk "{print $2}")'
alias drx='dnginxrestart'
alias du='du -kh'
alias dutop='du -ah | sort -hr | head'
alias dv='npm run dev'
alias dvls='docker volume ls'

// create and start containers
docker-compose up
// start services with detached mode
docker-compose -d up
// start specific service
docker-compose up <service-name>
// list images
docker-compose images
// list containers
docker-compose ps
// start service
docker-compose start
// stop services
docker-compose stop
// display running containers
docker-compose top
// kill services
docker-compose kill
// remove stopped containers
docker-compose rm
// stop all contaners and remove images, volumes
docker-compose down
```
