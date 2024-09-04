
The following steps needs to be done to enable the remote debugging.

Run the application. This will start the cap services. We need to login to the instance the service runs and tell the node js to enable remote debugging.

Step 1: Enable SSH Login to the Server. 

Step 2: ssh into the server

```
cf ssh <servername>
```

The log highlighted below will be registered on this step to inform you successfully ssh into the server.

<Image to be added>

Step 3: Find the process running the Server and kill the process with the flag -usr1 

To see the list of process running execute following command .

```
ps aux
```

```
kill -usr1 <pid>
```

Step 4: Enable Port forwarding. 

cf ssh -N -L 9229:127.0.0.1:9229 <servername>

Step 5: Add launch configuration 

```
    {
      "name": "Attach to a Cloud Foundry Instance on Port 9229",
      "port": 9229,
      "request": "attach",
      "type": "node",
      "localRoot": "${workspaceFolder}",
      "remoteRoot": "/home/vcap/app"
    }
```

Step 6: Place the break point and run the service. 
