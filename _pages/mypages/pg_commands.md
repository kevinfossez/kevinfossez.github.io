---
layout: archive
permalink: /misc/commands/
title: How-to bash
description: Last update on July 25, 2019
---


## Put files and directory rights to default values

```bash
find ../492A-5B6E/ \( -type f -execdir chmod 644 {} \; \) -o \( -type d -execdir chmod 755 {} \; \)
```

## Basic find command search

```bash
find where_to_search/ -name name_directory -type d
```

## Look (grep) for utf8 characters in files

```bash
grep --color='auto' -P -n "[\x80-\xFF]" file
```

## Rename files (extensions)

```bash
rename 's/\.cxx$/.cpp/' *.cxx
```

## Idem inside the text (like "includes" in C++)

```bash
grep -rl '\.cxx' ./ | xargs sed -i 's/\.cxx/\.cpp/g'
```

## Copy with a progression bar (and more)

```bash
rsync -av --delete-after --stats --progress to_save/ rep_where_to_save/
```

The options are:
- `-a` for recursive 
- `-v` for verbose 
- `--delete-after` to remove everything in "rep_where_to_sauv/" that is not present in "to_save/"
- `--stats` to show lots of information (not essential) 
- `--progress` to show a progression bar


## Vim command to search and replace in several files

```bash
vim
:args *.cpp *.h
:bufdo %s/pattern/replace/g | update
```

## Generate public and private ssh keys

```bash
ssh-keygen -t rsa
```

Give a name like "id_rsa_foo" and you get two files:
- id_rsa_foo --> private key
- id_rsa_foo.pub --> public key

Then copy the **public** key on the remote machine:

```bash
scp id_rsa_foo.pub username@remotemachine:/home/username/.ssh/
```

Add the key to the authorized host file:

```bash
cat id_rsa_foo.pub >> authorized_hosts
```

## Make a config file for ssh

In .ssh/, create a file named "config" and add a profile to make it easy to connect via ssh.

```bash
Host remMach
	HostName remoteMachineName
	User username
	IdentityFile ~/.ssh/id_rsa_foo
	ProxyCommand ssh remoteMachineName nc %h %p
```

Or even simpler depending on the case:

```bash
Host remMach
	HostName remoteMachineName.institute.edu
	User username
	PubkeyAuthentication no
```

Then to connect instead of:
```bash
ssh username@remoteMachineName.institute.edu
scp -r username@remoteMachineName.institute.edu:/mnt/home/username/dir/ .
```
 one can use:
```bash
ssh username@remMach
scp -r username@remMach:/mnt/home/username/dir/ .
```

## Create a torrent file

```bash
transmission-create -o ~/torrent_name.torrent -t udp://open.demonii.com:1337 -t udp://9.rarbg.com:2710/announce -t udp://tracker.openbittorrent.com:80/announce -p -c "comment" rep_to_share.zip
```

Different tracker addresses can be used, but beware what you share.

## Download a website

```bash
wget -r -l5 -k -E "http://www.l_adresse_du_site.a_recuperer.com"
```

Add the option `-c` to restart an incomplete download, or the option `-np` to avoid going up the directory tree to download a single page.

## Open a Jupyter notebook on MacOS

Install Jupyter using Homebrew, then:
```bash
jupyter notebook [location] &
```


