First build the docker image, updating the tag (`2.2.10-node`) if necessary:

```
docker build -t bespokepost/ruby:2.2.10-node .
```

After it is done building, run a shell with the image:

```
$ docker run -it 40891423986c /bin/bash
circleci@e1f83cca3923:~$ exit
```

Using the hash in the command line prompt, create a new commit and push:

```
docker commit e1f83cca3923 bespokepost/ruby:2.2.10-node
docker push bespokepost/ruby:2.2.10-node
```
