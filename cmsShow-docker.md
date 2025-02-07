# cmsShow (Fireworks) in VM (Virtual Box)

## 1. Install xquartz
```
brew install --cask --no-quarantine xquartz
defaults write org.xquartz.X11 nolisten_tcp -bool false
defaults write org.xquartz.X11 no_auth -bool false

mkdir -p ~/.xinitrc.d

cat << 'EOF' > ~/.xinitrc.d/xhost-config.sh
#!/bin/sh

xhost +localhost
xhost +\$(hostname)
EOF

chmod +x ~/.xinitrc.d/xhost-config.sh

xhost +localhost
xhost +127.0.0.1

defaults write org.xquartz.X11 enable_iglx -bool true
```

## 2. Install Docker Desktop on Mac
> https://docs.docker.com/desktop/setup/install/mac-install/

## 3.Make cmsShow Docker image
> https://github.com/alja/fireworks-docker?tab=readme-ov-file
```
wget https://cmsshow-rels.web.cern.ch/cmsShow-rels/cmsShow-13.3.tgz
docker build DockerFile
```
## 3. Install fireworks-docker
```
docker pull aljamrak/fireworks:cmsShow-11.2
```
## 4. Run fireworks-docker
```
docker run -it --rm \
    --platform=linux/amd64 \
    -e DISPLAY=host.docker.internal:0 \
    -v /tmp/.X11-unix:/tmp/.X11-unix:rw \
    aljamrak/fireworks:cmsShow-11.2
```


## 5. cmsShow command
```
./cmsShow -c /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/simGeo.fwc --sim-geom-file <geometry-file>

./cmsShow -c /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/simGeo.fwc --sim-geom-file /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/rpcf-2025-v2-addiRPCREm34.root 

./cmsShow -c /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/overlaps.fwc --sim-geom-file <geometry-file> 

./cmsShow -c /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/overlaps.fwc --sim-geom-file /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/rpcf-2025-v2-addiRPCREm34.root 

./cmsShow -c /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/overlaps.fwc --sim-geom-file /cmsShow-11.1.2/workspace-rpc-geom/250206-cmsshow/rpcf-2025-v2-finetunez-addiRPCREm34.root 
```