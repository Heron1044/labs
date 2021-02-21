### create a user on all machines ( controller & all targets )

	useradd hemanth -m -d /home/hemanth -s /bin/bash

### add user to sudoers for root previliges  on all machines ( all targets )

	echo -e 'hemanth ALL=(ALL)  NOPASSWD:  ALL' > /etc/sudoers.d/hemanth

### genereate ssh keys for above user on contrller machine 

```
	1) switch to user ( su - hemanth )
	2) run "ssh-keygen" command as user ( this will genereate ssh keys for the user ) 
```
```
        on ansible controller machine
		cd /home/hemanth/.ssh 
		cat id_rsa.pub (copy the content)
```
### copy user ssh keys from ansible contrller to all target hosts

```
	1) on all target machines
		   swith to the user ( su - hemanth )
		   mkdir -p /home/hemanth/.ssh
		   touch /home/hemanth/.ssh/authorized_keys
		   chmod -R 700 /home/hemanth/.ssh
		   vi /home/hemanth/.ssh/authorized_keys  (enter the copied contet of id_rsa.pub from controller & save the file)
```	
	

