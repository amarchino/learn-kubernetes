## Docker
```bash
docker run -d --name=redis redis:alpine
docker run -d --name=db -e POSTGRES_HOST_AUTH_METHOD=trust postgres:9.4.26-alpine
docker run -d --name=vote -p 5000:80 --link redis:redis kodecloud/examplevotingapp_vote:v1
docker run -d --name=result -p 5001:80 --link db:db kodecloud/examplevotingapp_result:v1
docker run -d --name=worker --link redis:redis --link db:db kodecloud/worker:v1
```

```
docker stop redis db vote result worker
docker rm redis db vote result worker
```