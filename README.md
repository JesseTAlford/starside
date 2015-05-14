# Read Me

This is an aspirational readme, just now. But let me tell you what this thing is going to be about.

The idea is to have a game played on [lattice.cf](http://lattice.cf). The principle gameplay is investigating and applying configuration details for a series of apps pushed to a lattice instance, which plays the role of a fictional compute cluster on a damaged space station. Happily, lattice's website basically looks like something out of science fiction already, which is a consideration in choosing it over some other Cloud Foundry technology for this purpose. Also, lattice's simple local deployment options mean that no one will have to get access to a Cloud Foundry instance or mess with BOSH to get started.

The initial plan for installation is to make it as minimal as possible, and include as much of what will be necessary as possible in a vagrant box. This does mean that users will have to install virtualbox and vagrant to get up and running - and unfortunately, vagrant means tangling with ruby. And git will be necessary.

After the vm is up, a player should be able to ssh in and have everything they need.

This is not possible with the current lattice box. Additional steps I think will be necessary:

1. Install the ltc CLI:

```
sudo wget https://lattice.s3.amazonaws.com/releases/latest/linux-amd64/ltc -O /usr/local/bin/ltc
chmod +x usr/local/bin/ltc
```

That... that may actually be it.

Well, there may be persistance-layer setup.

Lattice's containers use ephemeral disks. In order to have persistant state – and this game is going to need it – at least one database service is going to be necessary. Now, I assume the one-box, vagrant deployment of lattice is already running some kind of database server. I may be able to just use that. I mean, maybe writing a game that uses (I assume) etcd for persistance is crazy-talk? Then again, it might not be a whole lot of data.

Something to consider.

The initial product could probably be ready to show off with only two dockerized components: an "emergency status system" that lets you do error-driven development on your shattered station's systems and a "stasis chamber monitoring system" that lets you learn if any of your collegues might still be alive in the station's stasis banks, and what kind of trouble they might be in. You'd get the first one up by reading something like an "emergency response manual" and then be guided by its error messages from there. The first manual might also instruct you to check on your fellow crew – which of course means bringing up the stasis monitoring systems, which means hunting up some credentials and configuration options and deploying.

This, plus some short fiction setting up the scenario and a couple of sharp pieces of art, could be enough to get people excited about the idea.

