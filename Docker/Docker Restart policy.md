The following example starts a Redis container and configures it to always restart unless it is explicitly stopped or Docker is restarted.

```
$ docker run -d --restart unless-stopped redis
```

This command changes the restart policy for an already running container named `redis`.

```
$ docker update --restart unless-stopped redis
```

And this command will ensure all currently running containers will be restarted unless stopped.

```
$ docker update --restart unless-stopped $(docker ps -q)
```