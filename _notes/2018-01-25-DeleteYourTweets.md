---
layout: post
title: How to delete your tweets yourself, when you have a lot of tweets. 
date: 1969/01/01
colour: "#080808"
word-color: "#AAAAAA"
link-color: "white"
published: false
---
# {{ page.title }} 

1. Get api keys from apps.twitter.com

2. install t (by sferik)

3. request your archive from twitter.com/settings/account

4. wait for the archive to be sent to you

5. get the tweets.csv from the archive

6. authenticate t, or put your keys in .trc

7. delete the title line (first line in tweets.csv)

8. reverse the file so it goes through in reverse (rev is cool)

9. clean out the tweets by hand or another method, such that all the ones left are just the ones you want to delete

10. the first column is the tweet ids, so remove everything but that with something like:
> sed -e "s/[^0-9,]//g" | cut -d, -f1 | grep "^[0-9]" 

11. while read entry; do t delete status $entry && sed -e "/$entry/d" tweets.csv; done < <( cat tweets.csv )

12. then wait until its done
