# VAGRANT
https://www.vagrantup.com/

## Fixing crashed VAGRANT machine
I'm getting crashing troubles with VAGRANT, so I need to settle an emergency plan for this situation.

In every half year I wake up in a morning and notice my notebook completety freezed. In the most of cases this means VAGRANT has carshed, and I'will have a bad day again. 
I'm going through on this 4. time, but it still a real pain in the ass, so I wanna make an emergency plan for this.

### Getting into your VM
If a Vagrant VM has crashed you can't start your VAGRANT machine with a simple vagrant up command, you will get stucks, hangs, freezes, so let's avoid VAGRANT a little bit..

Go to Virtualbox, and start the VM from there. You will see what's happening, and maybe you will be able to reach some-kind of login screen.
I had to struggle a bit with this, because I got several mounting errors. I kept trying with pushing S (Skip) and M (solve it manually) through the error messages, and reboots finally I got a read-only filesystem with a login.

**If you still can't get into your VM you can try this awesome trick:

https://superuser.com/questions/947942/unprocessed-orphan-inode-list-in-virtualbox-vm

### Login into VM
If you have seen some kind of login screen, you can use these credentials:
```
username: vagrant
password: vagrant
```

### Back-up with read-only filesystem
Due I couldn't write the file-system it's a bit hard to make backups. 

So I **mounted a VM shared folder** from my PC so I was able to backup the files inside the Linux filesystem to my hard drive.

https://serverfault.com/questions/674974/how-to-mount-a-virtualbox-shared-folder

https://i.stack.imgur.com/Gu70v.png

`sudo mount -t vboxsf var_www /var/www/`

#### Backup files
**MYSQL**
Database files in system level (Debian):

`/var/lib/mysql/`

**Export**
```
mysqldump -u root -p --all-databases > alldb.sql
mysqldump -u root -p --opt --all-databases > alldb.sql
mysqldump -u root -p --all-databases --skip-lock-tables > alldb.sql
```

**Import**

`mysql -u root -p < alldb.sql`

**OTHER FILES/FOLDERS**

I usually save the `/home`,`/root` and `/etc` folders, they contains the most of neccessary files.

#### Export VM
VirtualBox GUI (no snapshots):

https://www.techrepublic.com/article/how-to-export-virtualbox-virtual-machines-as-appliances/

Command Line (no snapshots):

https://www.techrepublic.com/article/how-to-import-and-export-virtualbox-appliances-from-the-command-line/

With Snapshots:

https://superuser.com/questions/1184529/export-a-vm-with-the-snapshots

#### Moving Virtualbox Deeply (regedit changes and so..)
https://medium.com/@cedricdue/moving-vagrant-boxes-and-related-virtualbox-vms-to-another-drive-f1d7c50d20bc

#### Useful links
http://margotskapacs.com/2013/02/after-vagrant-crash-how-to-recover-database/

