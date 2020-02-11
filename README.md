## _Preparing_ ##
```
echo "HOST=pbshost" > ./.env
```
Defining the `HOST` variable is arbitrary. In this text, I define `pbshost`.


## _Building_ ##
```
docker-compose up -d
```


## _Lauching_ ##
```
$ docker run -h pbshost --name worker -itd cetusk/pbs-ubuntu16.04:latest
$ docker exec -it worker /bin/bash
```

## _Validation_ ##
Checking PBS profile:
```
root@pbshost:/# pbsnodes
pbshost
     state = down
     np = 4
     ntype = cluster
```
Running precompiled sample code. This container includes a sample code which is in `/home/test/` directory.
```
root@pbshost:/# cd home/test/
root@pbshost:/home/test# ls
run.sh  test  test.cpp
root@pbshost:/home/test# qsub run.sh
0.pbshost
root@pbshost:/home/test# qstat
Job id                    Name             User            Time Use S Queue
------------------------- ---------------- --------------- -------- - -----
0.pbshost                 pbs-test         root            00:00:00 C batch
root@pbshost:/home/test# ls
run.sh  test  test.cpp  test.stderr  test.stdout
root@pbshost:/home/test# cat test.stdout
test: proc id = 0 / 4
test: proc id = 1 / 4
test: proc id = 3 / 4
test: proc id = 2 / 4
```


---
## _History_ ##
_Ver.0.3 ( latest )_ @ 02.11.2020.Tue.: added libraries of Anaconda3, build-essential, OpenMPI, MKL  
_Ver.0.2_ @ 02.09.2020.Sun.: packaged minimal of torque system  
_Ver.0.1_ @ 02.09.2020.Sun.: initial commition  
