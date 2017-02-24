
    $ docker-machine start scaladock
    $ eval "$(docker-machine env scaladock)"
    $ docker-machine url scaladock | \
    >     perl -ne '@l=split(":");print split("/",@l[1]);print "\n";'

    $ docker build -t gnperdue/scaladock:0.1 .

    $ docker run -v $PWD:/root -it --rm gnperdue/scaladock:0.1

```
java8_scala2.12$ docker run -it --rm gnperdue/scaladock:0.1
root@0c2bb98008a7:~# ls
scala-2.12.1
root@0c2bb98008a7:~# pwd
/root
root@0c2bb98008a7:~# ls /
bin   dev  home  lib64 mnt  proc  run  srv  tmp  var
boot  etc  lib  media opt  root  sbin  sys  usr
root@0c2bb98008a7:~# ls scala-2.12.1/
bin  doc  lib  man
root@0c2bb98008a7:~# ls scala-2.12.1/bin/
fsc  scala     scalac scaladoc      scalap
fsc.bat  scala.bat  scalac.bat scaladoc.bat  scalap.bat
root@0c2bb98008a7:~# which scala
/root/scala-2.12.1/bin/scala
root@0c2bb98008a7:~# which sbt
/usr/bin/sbt
root@0c2bb98008a7:~# exit
exit

java8_scala2.12$ docker run -v $PWD:/work -it --rm gnperdue/scaladock:0.1
root@2b3607ee5dbf:~# ls
scala-2.12.1
root@2b3607ee5dbf:~# ls /
bin   dev  home  lib64 mnt  proc  run  srv  tmp  var
boot  etc  lib  media opt  root  sbin  sys  usr  work
root@2b3607ee5dbf:~# ls /work/
Dockerfile       failed_v2_Dockerfile    mellow.scala
failed_v1_Dockerfile  jdk-8u121-linux-i586.tar.gz  scala-2.12.1.tgz
root@2b3607ee5dbf:~# cd /work/

root@965749c227d9:/work# scalac mellow.scala
root@965749c227d9:/work# ls
Dockerfile         Mellow.class      mellow.scala
Dockerfile_worked        failed_v1_Dockerfile     scala-2.12.1.tgz
Mellow$.class         failed_v2_Dockerfile
Mellow$delayedInit$body.class  jdk-8u121-linux-i586.tar.gz
root@965749c227d9:/work# scala Mellow
Mellow, whirled

root@2b3607ee5dbf:/work# echo $JAVA_HOME
/usr/lib/jvm/java-8-openjdk-amd64
root@2b3607ee5dbf:/work# printenv | grep SCALA
SCALA_VERSION=2.12.1

root@2b3607ee5dbf:/work# javac -version
javac 1.8.0_121
root@2b3607ee5dbf:/work# which java
/usr/bin/java
```

Work with 2.11 for now

```
java8_scala2.11$ docker build -t gnperdue/scaladock:8.2.11.7 .
java8_scala2.11$ docker push gnperdue/scaladock:8.2.11.7
java8_scala2.11$ docker build -t gnperdue/scaladock:latest .
java8_scala2.11$ docker push gnperdue/scaladock:latest
```

Workflow example:

```
docker-machine start scaladock
eval "$(docker-machine env scaladock)"
docker pull gnperdue/scaladock
docker run -v $PWD:/work -it --rm gnperdue/scaladock

root@5c13f2977db1:~# cd /work/
root@5c13f2977db1:/work# scala
Welcome to Scala version 2.11.7 (OpenJDK 64-Bit Server VM, Java 1.8.0_121).
Type in expressions to have them evaluated.
Type :help for more information.

scala>
```
