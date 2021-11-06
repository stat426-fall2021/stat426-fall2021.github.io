---
title: Cancelling Noise in Data: Image Compression Tutorial
layout: post
author: jessica-hamblin
post-image: /assets/images/blogimages/figs-09-13/github-ssh-pic.png
description: Short tutorial about setting up SSH keys for GitHub.
tags:
- image compression
- reduction
- linear algebra
- svd
- noise
---

One common problem  in data science is that our data is noisy. A good data scientist 
is able to distinguish between that noise and signal in the data. One great way 
to "cancel noise" in data represented in matrix form is to use singular value decomposition 
from linear algebra.

# Linear Algebra
Let me explain some key concepts first.
<div class="tenor-gif-embed" data-postid="14688422" data-share-method="host" data-aspect-ratio="1.84971" data-width="100%"><a href="https://tenor.com/view/let-me-explain-no-too-much-gif-14688422">Let Me Explain No GIF</a>from <a href="https://tenor.com/search/let+me+explain-gifs">Let Me Explain GIFs</a></div> <script type="text/javascript" async src="https://tenor.com/embed.js"></script>

Singular value decomposition (SVD) is a method that breaks a matrix into three less-complicated
matrices. One convenient feature of these three matrices is that the values inside them are 
sorted such that the most important attributes come at the beginning-- that makes it easy to 
extract the features that hold the most predictive power.

With that in mind, it's no wonder that Benjamin Obi Tayo, Ph.D. wrote on [KDnuggets](https://www.kdnuggets.com/2021/05/essential-linear-algebra-data-science-machine-learning.html): 
"Linear algebra is the most important math skill in machine learning."

Now let's take a look at an example of how to use SVD to reduce image sizes.

# Tutorial
1. Open up a new notebook your favorite python editor. I like to use Jupyter notebooks, but Google Colab is also a great option if you
don't have python downloaded on your computer.
2. 









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

![screenshot](/assets/images/blogimages/figs-09-13/github-ssh.png)


## Attributions
Cover photo by <a href="https://unsplash.com/@cetteup?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">cetteup</a> on <a href="https://unsplash.com/s/photos/ear-plugs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>.
This post is adapted from a lab from the Computational Linear Algebra class at 
  
