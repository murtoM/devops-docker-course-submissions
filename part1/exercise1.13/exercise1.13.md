# 1.13: Hello, backend! 

Commands:
```
$ git clone --depth 1 https://github.com/docker-hy/material-applications.git

$ cd material-applications/example-backend/
```

Dockerfile:
```
FROM debian:stable-slim
EXPOSE 8080
WORKDIR /backend

# install prerequisites
RUN apt-get update && apt-get install -y curl
RUN rm -rf /usr/local/go && curl -sL https://golang.org/dl/go1.15.10.linux-amd64.tar.gz | tar -C /usr/local -xzf -
ENV PATH=$PATH:/usr/local/go/bin

# copy the project to the image
COPY . .

# build the project
RUN go build

CMD ["./server"]
```

Commands:
```
$ docker build . -t example-backend

$ docker run -it -p 80:8080 example-backend

$ curl localhost/ping
pong
```

