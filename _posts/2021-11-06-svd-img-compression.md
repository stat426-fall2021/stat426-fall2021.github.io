---
title: "Cancelling Noise in Data: Image Compression Tutorial"
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
<div class="tenor-gif-embed" data-postid="8939664" data-share-method="host" data-aspect-ratio="1.86047" data-width="100%"><a href="https://tenor.com/view/let-me-explain-sum-up-too-much-i-just-cant-princess-bride-gif-8939664">Let Me Explain Sum Up GIF</a>from <a href="https://tenor.com/search/let+me+explain-gifs">Let Me Explain GIFs</a></div> <script type="text/javascript" async src="https://tenor.com/embed.js"></script>


Singular value decomposition (SVD) is a method that breaks a matrix into three less-complicated
matrices. One convenient feature of these three matrices is that the values inside them are
sorted such that the most important attributes come at the beginning-- that makes it easy to
extract the features that hold the most predictive power. If you want to take a deeper dive into
linear algebra and how it will help you be a better data scientist, check out this excellent blog post from
[Toward Data Science](https://towardsdatascience.com/understanding-singular-value-decomposition-and-its-application-in-data-science-388a54be95d)!

With that in mind, it's no wonder that Benjamin Obi Tayo, Ph.D. wrote on [KDnuggets](https://www.kdnuggets.com/2021/05/essential-linear-algebra-data-science-machine-learning.html):
"Linear algebra is the most important math skill in machine learning." Let's take a look at an example of how to use SVD to reduce image sizes!

# Tutorial
1. Open up a new notebook your favorite python editor. I like to use Jupyter notebooks, but Google Colab is also a great option if you
don't have python downloaded on your computer.
2. Download a PNG image to play with. I'll use this one: ![dog](/assets/images/blogimages/figs-11-06/oscar-sutton-yihlaRCCvd4-unsplash.png)
3. If you're using Jupyter, add the photo to the same directory as your notebook. If you're
using Colab, go to the left sidebar, and click the "Upload to session storage" button. You'll have to do this each time you
close the notebook and come back to it later.
![upload-to_colab](/assets/images/blogimages/figs-11-06/colab_upload_img.PNG)
4. In the first cell, add these imports:
```python
   import numpy as np
   import skimage
   from skimage import io
   import matplotlib.pyplot as plt
   ```
5. Now we need to read in our image file as a python array. You can choose whether to keep it as a color (RGB) image
or convert it to grayscale.
```python
color_array = io.imread('dog.png')            
gray_array = skimage.color.rgb2gray(color_array)
```
6. Now that we have our images, let's define some functions that will plot an array as an image to help us see what we have.
```python
def show_color(array):
    # set up the matplotlib figure
    plt.figure(figsize=(10,10))
    # optional-add grid lines to figure
    plt.grid(None)
    # show the array as an image within the figure
    plt.imshow(array)
    return None

def show_gray(array):
    # set up the matplotlib figure
    plt.figure(figsize=(10,10))
    # optional-add grid lines to figure
    plt.grid(None)
    # show the array, but specify that the color map is gray with a min val of 0 (white) and max of 1 (black)
    plt.imshow(array,cmap='gray',vmin=0,vmax=1)
    return None
```
7. Test your functions by printing out either or both the color and grayscale images. For the rest of the tutorial,
I will use the grayscale image.
```python
show_color(color_array)
show_gray(gray_array)  
```
8. Now let's calculate the number of values in this matrix by multiplying the number of rows by the number of columns.
```python
m,n = gray_array.shape
original_size = m*n
print(original_size)
```
9. Now we can call the `svd` function to decompose `gray_array` into three matrices. Typically, these three matrices are
called `U`, `Sigma`, and `V^t` so we will name them accordingly. If we wanted to, we could use these to reconstruct an
approximation of `gray_array`.
```python
u_orig,s_orig,v_t_orig = np.linalg.svd(gray_array)
```
In reality, `s_orig` is actually a 1-dimensional array instead of a matrix (2-dimensional array). This is because
the `Sigma` matrix has 0's everywhere except the diagonal from the top left corner, so we only need one dimension to
contain all the nonzero values, which are called "singular values." These are arranged from largest to smallest.

10. Graph the singular values in `s_orig` against their index in the array. This will let us get a good idea how many
singular values we will need to make a good approximation of our image without losing too much quality.
```python
plt.plot(s_orig)
```
![plot](/assets/images/blogimages/figs-11-06/plot.PNG)
Since the line drops to nearly 0 when x (index) is still very small, this means that we will be able to make a good
approximation using just a few of the singular values.

11. In order to reconstruct our reduced-size image matrix, we're going to need to define a few functions.
The first is a function that takes in two ints that represent the number of rows and columns as well as an array of
singular values, and returns a `Sigma` matrix.
```python
def sigma(m,n,s):
  E = np.zeros((m,n))
  for i in range(0,len(s)) :
    E[i,i] = s[i]
  return E
```
That creates a matrix of the correct size filled with 0's, and then goes along the diagonal and changes the 0 to the
corresponding singular value from `s`.

12. The second function takes in a 2D array `u`, a 1D array `s`, and a 2D array `v_t`, which correspond to the 3 outputs
from calling `svd`. It multiplies them together to reconstruct a single matrix.
```python
def reconstructed_array(u,s,v_t):
  sgm = sigma(len(u[0]),len(v_t),s)
  usgm = np.matmul(u,sgm)
  usgmvt = np.matmul(usgm,v_t)
  return usgmvt
```

13. The third function brings everything together to produce a rank `k` approximation of a matrix `A`. That essentially
translates to keeping a matrix with only the top `k` singular values.
```python
def lower_rank(A,k):
  u,s,v_t = np.linalg.svd(A)
  u_k = u[:,:k]
  v_t_k = v_t[:k,:]
  s_k = s[:k]
  return reconstructed_array(u_k,s_k,v_t_k)
```

14. Now you can plug in different values of `k` into your function along with our original `gray_array` and you can
decide what value of `k` you think is best. The smaller the value of `k`, the more compressed our final image will be,
but be careful to not make it too fuzzy. The best value will vary for different pictures.
```python
k = [choose a value]
gray_reduced = lower_rank(gray_array, k)
show_gray(gray_reduced)
```

15. As it is right now, `gray_reduced` has the exact same dimensions as the original `gray_array` matrix. However, now
we can call `svd` on `gray_reduced` and we can get rid of anything we don't need. In reality, we only need the first `k`
only need the first `k` columns of `u`, the first `k` rows of `v_t`, and the first `k` values of `sigma`. That will tell
us how many values we really need to represent the image. We can use that to find the number of values we need.
```python
u_reduced,s_reduced,v_t_reduced = np.linalg.svd(gray_reduced)
reduced_size = ((len(u_reduced[0]) * k) + (len(v_t_reduced) * k) + k)
print("Reduced size: ", reduced_size)

relative_size= reduced_size/original_size
print("Original size: ", original_size)
print("Reduced size is what percent of original size: ", relative_size)
```













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
