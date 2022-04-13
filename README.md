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
