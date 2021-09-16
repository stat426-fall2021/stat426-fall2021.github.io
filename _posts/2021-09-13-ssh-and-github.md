---
title: Using SSH with GitHub
layout: post
author: shannon_tass
post-image: "https://raw.githubusercontent.com/stat426-fall2021/stat426-fall2021.github.io/01691d6f3977d01eb138982573d1ae44381f9adf/assets/images/blogimages/github-ssh.png"
description: Short tutorial about setting up SSH keys for GitHub.
tags:
- ssh
- git
- github
---


This post is adapted from the GitHub documentation page
[Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh).

You can use the SSH protocol by setting up SSH keys to connect with GitHub without
needing to supply your username and access token.  SSH stands for Secure Shell
and it protocol for operating network services securely over an unsecured network.
You can read more about SSH [here](https://en.wikipedia.org/wiki/Secure_Shell).

# Check for existing SSH keys
1. Open the terminal (Mac) or Git Bash (Windows)
2. Enter ```ls -la ~/.ssh```
3. Check the directory listing to see if you have a public SSH key, usually:  

   * id_rsa.pub
   * id_ecdsa.pub
   * id_ed25519.pub

4. If you receive an error that ~/.ssh doesn't exist, then you don't have ssh keys

# Generating New SSH Keys
*(If you already have SSH keys, skip to the next section.)*

Below are instructions for generating SSH keys.  When doing this, you have the choice of an algorithm to use (with the `-t` option) and the key size (with the `-b` option).  You can read more about SSH keys and the different algorithm/key size options [here](https://www.ssh.com/academy/ssh/keygen).  The instructions below use the rsa algorithm with a 4096 bit key size.


1. Open the terminal (Mac) or Git Bash (Windows)
2. In the terminal type  
```ssh-keygen -t rsa -b 4096 -C "your_github_email@email.com"```   
(be sure to use your actual GitHub email address)
3. When you are prompted to "Enter a file in which to save the key", just press enter to accept the default location
4.  Add a passphrase for extra security or press enter for no passphrase

# Adding SSH Keys to your GitHub Account

1. Copy the SSH public key to the clipboard.  
```cat ~/.ssh/id_rsa.pub```
will show you the public key and you can copy it.
2. Go to GitHub.  In the upper-right corner, click on your profile photo, then click **Settings**.  
3. In the user settings sidebar, click *SSH and GPG keys*
4. Click **New SSH key**
5. In the "Title" field, add a label for your key.  For example "Personal MacBook Air"
6. Paste your key into the "Key" field.
7. Click **Add SSH key**.

# Using SSH Key
In GitHub, when cloning repositories, or setting up the remote repository, use SSH instead of HTTP:

![screenshot](/assets/images/blogimages/github-ssh.png)
