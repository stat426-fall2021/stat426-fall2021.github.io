title: How to scrape song lyrics in R: a webscraper for beginners
layout: post
author: rachel-hammy
post-image: https://github.com/rachel-hammy/stat426-fall2021.github.io/blob/main/assets/images/blogimages/figs-11-15/raphael-lovaski-RjD01Is-KnI-unsplash.jpg
description: A step-by-step walkthrough of how to scrape song lyrics from azlyrics.com for beginners in R.
tags:
- webscraping
- lyrics
- tutorial
---

# How to scrape song lyrics in R: a webscraper for beginners

Words are data, and some of the most influential words in pop culture are song lyrics.  In order to conduct any sort of word analysis, first you need the words to the song.  

Luckily for us, azlyrics.com has an extremely organized and simple structure for all of their song lyric code on their webpage. Take a minute to observe the pattern of code for "Love Story" by Taylor Swift.

Note: You can view this same code by going to this url (https://www.azlyrics.com/lyrics/taylorswift/lovestory.html) and pressing Ctrl + u.  A new tab will open showing the html code for the website. The lyrics start around line 150.

```{r}
<b>"Love Story"</b><br>
<br>

<div>
<!-- Usage of azlyrics.com content by any third-party lyrics provider is prohibited by our licensing agreement. Sorry about that. -->
We were both young when I first saw you<br>
I close my eyes and the flashback starts:<br>
I'm standing there<br>
On a balcony in summer air<br>
<br>
See the lights, see the party, the ball gowns<br>
See you make your way through the crowd<br>
And say, &quot;Hello.&quot;<br>
Little did I know<br>
<br>
That you were Romeo, you were throwing pebbles<br>
And my daddy said, &quot;Stay away from Juliet.&quot;<br>
And I was crying on the staircase<br>
Begging you, &quot;Please don't go.&quot;<br>
And I said<br>
<br>
&quot;Romeo, take me somewhere we can be alone<br>
I'll be waiting. All there's left to do is run<br>
You'll be the prince and I'll be the princess<br>
It's a love story. Baby, just say 'Yes'.&quot;<br>
<br>
So, I sneak out to the garden to see you<br>
We keep quiet 'cause we're dead if they knew<br>
So, close your eyes<br>
Escape this town for a little while<br>
Oh, oh<br>
<br>
'Cause you were Romeo. I was a scarlet letter<br>
And my daddy said, &quot;Stay away from Juliet.&quot;<br>
But you were everything to me<br>
I was begging you, &quot;Please don't go!&quot;<br>
And I said<br>
<br>
&quot;Romeo, take me somewhere we can be alone<br>
I'll be waiting. All there's left to do is run<br>
You'll be the prince and I'll be the princess<br>
It's a love story. Baby, just say 'Yes'<br>
<br>
Romeo, save me. They're trying to tell me how to feel<br>
This love is difficult but it's real<br>
Don't be afraid. We'll make it out of this mess<br>
It's a love story. Baby, just say 'Yes'.&quot;<br>
<br>
Oh, oh, oh<br>
<br>
I got tired of waiting<br>
Wondering if you were ever coming around<br>
My faith in you was fading<br>
When I met you on the outskirts of town<br>
And I said<br>
<br>
&quot;Romeo, save me. I've been feeling so alone<br>
I keep waiting for you, but you never come<br>
Is this in my head? I don't know what to think.&quot;<br>
He knelt to the ground and pulled out a ring and said<br>
<br>
&quot;Marry me, Juliet. You'll never have to be alone<br>
I love you, and that's all I really know<br>
I talked to your dad. Go pick out a white dress<br>
It's a love story. Baby, just say 'Yes'.&quot;<br>
<br>
Oh, oh, oh, oh, oh, oh<br>
<br>
'Cause we were both young when I first saw you
</div>

```

Because of its consistency, we will be able to create a scraper that outputs lyrics for any song / artist combination that's listed on their website.  Here’s how to make a beginning web scraper scrape any song lyrics you’d like:

### Step 1

First, lets import the tidyverse.
```{r}
library(tidyverse)
```
### Step 2

We need to find a way to produce the song's unique url on azlyrics.com using only the artist name and song title.

The urls on AZlyrics.com have a very specific pattern to them.  They look like this:

  https://www.azlyrics.com/lyrics/taylorswift/backtodecember.html

  https://www.azlyrics.com/lyrics/edsheeran/shapeofyou.html

  https://www.azlyrics.com/lyrics/adele/easyonme.html

Notice the pattern?  Because AZlyrics has a distinct pattern for their URL, we can generate unique web lyric pages easily with just an artist name and song title.


https://www.azlyrics.com/lyrics/ + artist + / + song + .html

Which we can paste together like this:

```{r echo=TRUE}
artist <- "taylorswift"
song <- "lovestory"

my_url <- str_c("https://azlyrics.com/lyrics/", artist, "/", song, ".html")
```

### Step 3

Next, we need to pick where to start scraping.  In this case, every page of html code on AZlyrics contains “prohibited by our licensing agreement. Sorry about that.” on the line before the lyrics begin.  We will use this to show the scraper where to start scraping, and title it our "giveaway".

```{r}
giveaway <- "prohibited by our licensing agreement. Sorry about that."
```

Also, note that every page of code marks the end of the lyrics with “</div>”.  We will use this in our final code to show the scraper where to stop scraping from.
```{r}
# get starting line
start <- grep(giveaway, read_lines(my_url)) + 1 # start at line after giveaway

# get ending line
end <- grep("</div>", read_lines(my_url)[start:length(read_lines(my_url))])[1] + start
```

### Step 4

Last, we use all the pieces we have put together so far to read each line of lyrics from start to end, and paste them all together.
```{r}
paste(gsub("<br>|</div>", "", read_lines(my_url)[start:end]), collapse = " ")
```

### Putting it all together

Here is the complete function that will get lyrics for any song:
```{r}
# Function to get lyrics from any artist
getlyrics <- function(artist, song){
  giveaway <- "prohibited by our licensing agreement. Sorry about that."
  my_url <- str_c("https://azlyrics.com/lyrics/", artist, "/", song, ".html")
  start <- grep(giveaway, read_lines(my_url)) + 1 # start at line after giveaway
  end <- grep("</div>", read_lines(my_url)[start:length(read_lines(my_url))])[1] + start
  paste(gsub("<br>|</div>", "", read_lines(my_url)[start:end]), collapse = " ")
}

```

Now all we have to do whenever we want song lyrics is input an artist name and song title into our function.

```{r}
getlyrics("taylorswift", "lovestory")
```
Gives the following output:
```{r echo=TRUE}
 [1] "We were both young when I first saw you"              
 [2] "I close my eyes and the flashback starts:"            
 [3] "I'm standing there"                                   
 [4] "On a balcony in summer air"                           
 [5] ""                                                     
 [6] "See the lights, see the party, the ball gowns"        
 [7] "See you make your way through the crowd"              
 [8] "And say, &quot;Hello.&quot;"                          
 [9] "Little did I know"                                    
[10] ""                                                     
[11] "That you were Romeo, you were throwing pebbles"       
[12] "And my daddy said, &quot;Stay away from Juliet.&quot;"
[13] "And I was crying on the staircase"                    
[14] "Begging you, &quot;Please don't go.&quot;"            
[15] "And I said"                                           
[16] ""                                                     
[17] "&quot;Romeo, take me somewhere we can be alone"       
[18] "I'll be waiting. All there's left to do is run"       
[19] "You'll be the prince and I'll be the princess"        
[20] "It's a love story. Baby, just say 'Yes'.&quot;"
[21] ""                                                     
[22] "So, I sneak out to the garden to see you"             
[23] "We keep quiet 'cause we're dead if they knew"         
[24] "So, close your eyes"                                  
[25] "Escape this town for a little while"                  
[26] "Oh, oh"                                               
[27] ""                                                     
[28] "'Cause you were Romeo. I was a scarlet letter"        
[29] "And my daddy said, &quot;Stay away from Juliet.&quot;"
[30] "But you were everything to me"                        
[31] "I was begging you, &quot;Please don't go!&quot;"      
[32] "And I said"                                           
[33] ""                                                     
[34] "&quot;Romeo, take me somewhere we can be alone"       
[35] "I'll be waiting. All there's left to do is run"       
[36] "You'll be the prince and I'll be the princess"        
[37] "It's a love story. Baby, just say 'Yes'"              
[38] ""                                                     
[39] "Romeo, save me. They're trying to tell me how to feel"
[40] "This love is difficult but it's real"                 
[41] "Don't be afraid. We'll make it out of this mess"      
[42] "It's a love story. Baby, just say 'Yes'.&quot;"       
[43] ""                                                     
[44] "Oh, oh, oh"                                           
[45] ""                                                     
[46] "I got tired of waiting"                               
[47] "Wondering if you were ever coming around"             
[48] "My faith in you was fading"
[49] "When I met you on the outskirts of town"              
[50] "And I said"                                           
[51] ""                                                     
[52] "&quot;Romeo, save me. I've been feeling so alone"     
[53] "I keep waiting for you, but you never come"           
[54] "Is this in my head? I don't know what to think.&quot;"
[55] "He knelt to the ground and pulled out a ring and said"
[56] ""                                                     
[57] "&quot;Marry me, Juliet. You'll never have to be alone"
[58] "I love you, and that's all I really know"             
[59] "I talked to your dad. Go pick out a white dress"      
[60] "It's a love story. Baby, just say 'Yes'.&quot;"       
[61] ""                                                     
[62] "Oh, oh, oh, oh, oh, oh"                               
[63] ""                                                     
[64] "'Cause we were both young when I first saw you"
```

Note: In order to create the correct url, all artist names and song titles must be all lowercase and not contain spaces.  For example, instead of "Taylor Swift" we will input "taylorswift" as our artist.  We could easily write code to fix this as a next step, but for now our scraper is working just fine for a beginner web scraper.

Note:  When using this scraper on a large scale, I have occasionally been temporarily blocked from scraping on the azlyrics website.  In my experience this has only happened when looping through many songs, and I regain access within a few hours.
