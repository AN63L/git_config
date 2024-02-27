# Guide to setting up multiple git configs

This method has been tested on Windows but not on MacOS, however the method used should work for all platforms. 

## Intro 

This is a simple guide to setup multiple git configs, particularly useful when you use the same laptop to access your work and personal git repositories. 

This configuration allows you to have a different user and separate access keys.

## File structure

All the files you need are located in the ``config`` directory. 

You should place these files in the relevant directory on your computer (make sure to keep a copy of your old config file somewhere safe just in case): 
- For windows, in the user's root directory (e.g ``C:\Users\<username>``)
- For MacOS, in the  ``.config`` folder located in the user's root directory (e.g ``Users/<username>/.config/git/``) 

The git configuration file is stored at ``$HOME/.gitconfig`` on all platforms.

If you have trouble accessing your git config, simply run ``git config``

The ``.gitconfig`` file acts as the master git configuration, just like your standard ``.gitconfig`` file. 

Each configuration will have it's own unique ``.gitconfig`` file, making sure that each name is unique and not ``.gitconfig``

## Setup

For each separate configuration you wish to setup, simply add the following in your ``.gitconfig`` file: 

```
[includeIf "gitdir/i:<path to directory>"]
    path = <path to relevant git config>
```

For example:

```
[includeIf "gitdir/i:C:/Users/User/Documents/work/"]
    path = C:/Users/User/.gitconfig-work
```

For each config file, specify the user like below: 

```
[user]
	name = <Work git username>
	email = <Work git email>
```

For example: 

```
[user]
	name = John Doe
	email = john@gmail.com
```

By default the same key will be used for all the configs you specify. Optionally, you can also specify a unique ssh key with:

```
[core]
sshCommand = ssh -i <path to key>
```

For example:

```
[core]
sshCommand = ssh -i ~/.ssh/id_rsa_work
```