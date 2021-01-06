Install Docker Machine
```
base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  mkdir -p "$HOME/bin" &&
  curl -L $base/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe" &&
  chmod +x "$HOME/bin/docker-machine.exe"
```
  

```
docker-machine create \
    --digitalocean-region "nyc1" \
    --driver digitalocean \
    --digitalocean-size "2gb" \
    --digitalocean-access-token $DIGITAL_OCEAN_ACCESS_TOKEN \
    runner-node;
```

Install [doctl](https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/)
```
Invoke-WebRequest https://github.com/digitalocean/doctl/releases/download/v1.54.0/doctl-1.54.0-windows-amd64.zip -OutFile ~\doctl-1.54.0-windows-amd64.zip
```
Next, extract the binary by running:
```
Expand-Archive -Path ~\doctl-1.54.0-windows-amd64.zip
```
```
Move-Item -Path doctl-1.54.0-windows-amd64/doctl.exe -Destination C:\\Users\\Larry\\Dropbox\\utils
```
Use the API token to grant doctl access to your DigitalOcean account. Pass in the token string when prompted by doctl auth init, and give this authentication context a name.
```
doctl auth init --context docker
```

Authentication contexts let you switch between multiple authenticated accounts. You can repeat steps 2 and 3 to add other DigitalOcean accounts, then list and switch between authentication contexts:

```bigquery
doctl auth list
doctl auth switch --context <NAME>
```

```
docker tag frontend registry.digitalocean.com/orgtec/frontend
doctl registry login
docker push registry.digitalocean.com/orgtec/frontend
```
