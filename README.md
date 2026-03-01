# node-red-lab

this repo is for evaluating node-red usability/extendibility outside the IOT domain.

node-red 
- has a nice graphical workflows editor
- is written and can be extended with JavaScript
- good for API + IoT, is it suitable for other domain?

quick start
- run the container:
```
docker run -it -p 1880:1880 -v node_red_data:/data --name node-red-lab nodered/node-red
```
- open browser at: ```http://localhost:1880/```
- import workflows (menu top rigth) from one the file in ```./flows```



- can add node, e.g. k8s client:
```npm install --save node-red-contrib-kubernetes-client
```
- import/export workflows in JSON format

- can create custom nodes: https://nodered.org/docs/creating-nodes/

## Notes 
- tested only on following stack
  - Rasberry pi5 8GB RAM, no AI module (Pi AI HAT+)
  - Debian GNU/Linux 12 (bookworm)
  - ...
- to save a workflow klick 'deploy', not very intuitive :-)

- some flows perform JSON schema validation. You need node-red-contrib-ajv installed 
I built a custom image with node-red-contrib-ajv. Other method didn't work for me

Dockerfile
```
FROM nodered/node-red
RUN npm install --unsafe-perm --no-update-notifier --no-fund --only=production \
    node-red-contrib-ajv
```
then ```docker build -t my-node-red .```

