# node-red 

this lab is for evaluating node-red usability/extendibility outside the IOT doman.

node-red 
- graphical workflows editor
- written and can be extended with JavaScript
- good for API + IoT
- start with:
```
docker run -it -p 1880:1880 -v node_red_data:/data --name node-red-lab nodered/node-red
```
- open browser at: ```http://localhost:1880/```
- can add node, e.g. k8s client: 
```npm install --save node-red-contrib-kubernetes-client
```
- import/export workflows in JSON format

- can create custom nodes: https://nodered.org/docs/creating-nodes/

Note: to save a workflow klick 'deploy', not very intuitive :-)

create custom image with node-red-contrib-ajv installed.
Dockerfile
```
FROM nodered/node-red
RUN npm install --unsafe-perm --no-update-notifier --no-fund --only=production \
    node-red-contrib-ajv
```
then ```docker build -t my-node-red .```

