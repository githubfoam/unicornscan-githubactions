# unicornscan-githubactions
~~~~

$ git clone https://github.com/githubfoam/unicornscan-githubactions.git
$ docker build -t unicornscan/kalilinux . --file unicornscan-githubactions/dockerfiles/Dockerfile.kali.unicornscan
$ docker image ls
REPOSITORY               TAG       IMAGE ID       CREATED              SIZE
unicornscan/kalilinux    latest    23fcc045b93b   About a minute ago   359MB
$ docker run unicornscan/kalilinux:latest -h

$ docker run --name unicorntest unicornscan/kalilinux:latest 10.10.8.1
Send exiting ack, parent died?: system error No such file or directory
Recv exiting ack, parent died?: system error No such file or directory
$ docker container ls                                                                                                                                                        1 ⨯
CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS          PORTS     NAMES
85bb4ea0da38   unicornscan/kalilinux:latest   "unicornscan 10.35.8…"   30 seconds ago   Up 29 seconds             unicorntest
$ docker stop unicorntest
~~~~
troubleshooting
~~~~
$ cat unicornscan-githubactions/dockerfiles/Dockerfile.kali.unicornscan
FROM kalilinux/kali-rolling
LABEL org.opencontainers.image.authors="githubfoam"


RUN set -xe && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get -qq update && \
    apt-get -qqy upgrade

RUN set -xe && \
    apt-get install unicornscan -y


#ENTRYPOINT ["unicornscan"]
#CMD ["-h"]


$ docker build -t unicornscan/kalilinux:v1 . --file unicornscan-githubactions/dockerfiles/Dockerfile.kali.unicornscan

$ docker run -it --name test_unicornscan unicornscan/kalilinux:v1                                               125 ⨯
┌──(root㉿4b61dde11d7e)-[/]


─(root㉿4b61dde11d7e)-[/]
└─# unicornscan -h

~~~~
