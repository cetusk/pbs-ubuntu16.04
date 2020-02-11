## _Installation_ ##

```
$ docker pull cetusk/pbs-ubuntu16.04:latest
```
or if you want to install the minimal environment
```
$ docker pull cetusk/pbs-ubuntu16.04:0.2
```

## _Lauching_ ##
```
$ docker run -h pbshost --name worker -itd cetusk/pbs-ubuntu16.04:latest
$ docker exec -it worker /bin/bash
```

## _Validation_ ##
```
root@pbshost:/# pbsnodes
pbshost
     state = down
     np = 4
     ntype = cluster
```

---
## _History_ ##
_Ver.0.3 ( latest )_ @ 02.11.2020.Tue.: added libraries of Anaconda3, build-essential, OpenMPI, MKL  
_Ver.0.2_ @ 02.09.2020.Sun.: packaged minimal of torque system  
_Ver.0.1_ @ 02.09.2020.Sun.: initial commition  
