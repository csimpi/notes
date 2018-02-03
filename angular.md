# Angular 5
Let's see what we've got

## First steps
When I met the AngularJS it was a true love, it helped a lot to avoid a lot of unnecessary coding. jQuery were great for long time but nowadays just outdated.
Now I'll try to switch to Angular let's see what we've got.

## VAGRANT + Scotchbox.io
I built a very robust project managing and deploy system with Scotchbox VAGRANT box, and gitLab standalone server, so I wanna continue to use that with angular.
So I have an outdated system, I need upgrade npm, and node to install Angular 5.

I got many troubles with this very easy task. Basically, I'm not a nodejs guy, just not my type, I'm running into deep issues, long struggles several times during working with it, but I keep trying.

What I did?
Based on nodejs's docs I installed npm:
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs

I got outdated npm, and node versions.

I updated and upgraded npm.

I got ERROR messages about npm no longer works with node 5.

After some googleing, I installed nvm.
https://stackoverflow.com/questions/47158554/how-to-upgrade-npm-to-latest-from-v5-4-1-after-i-have-installed-nodejs-v9-0-0

https://github.com/creationix/nvm#install-script
I still got the ERROR about npm no loger works with node 5.

I uninstalled node.
sudo apt-get autoremove node

Reinstall node with nvm
nvm install 9
