---
layout: post
permalink: /projects/alive/
title: I am awake, I am alive, I am orange
date: 2016/10/30
colour: darkorange
link-color: white
type: life canary
continuous: true
---
# I am awake
# I am alive
# I am orange

---

From around December 2012 I started tweeting the phrase I am awake/I am alive.
This evolved slowly (becoming fully realised in April of 2013) into a 3 phrase
mantra that I tweet somewhat often.

On 2016/10/30 I decided to turn this practise into a practical verification of
identity using a Git repo and GPG signed commits of the readme. I believe this
is both a way of storing changes in my mind over time and also as a
verification that these words come from me. You can read the git over on my
[github]

---
{: .thick-rules}

# How to verify me being alive (my signature of this project)

---

## Ingredients:
* A computer with Bash or a shell like Debian or macOS
* GnuPG
* Git
* curl

To verify this is me you can find my public key either at [keybase] or by
searching a keyserver / pool for my fingerprint either printed on my business
card, [twitter], or simply "105C A1F4 AF75 DFE3 04AD  C68B 7181 6DF5 3240
20E9".  or if you have curl just grab it with 
> curl https://keybase.io/ff4500/pgp_keys.asc | gpg --import
> git clone https://github.com/ixt/I-am-awake-I-am-alive-I-am-orange   

the above command will download the git repo with the history of my signing  

> git verify-commit master  
the above command prints out the raw proof of signiture   

The print out will look something like what is below:  
> gpg: Signature made Sun 25 Dec 2016 20:34:32 GMT
> gpg:                using RSA key 012E450A25405E4004C81B2C6B35D47864E747E3
> gpg: Good signature from "NfN Orange <orange@ff4500.red>"

As long as it reads good signature that is signed with the key you downloaded
before. 
You need to have an aspect of your own trust about the place you
downloaded it from, comparing to my fingerprint using "gpg --fingerprint
orange@ff4500.red" to a copy you have from a business card is a good way to
check for authenticity or the next best thing is comparing the proofs on
keybase  

[github]: https://github.com/ixt/I-am-awake-I-am-alive-I-am-orange
[keybase]: https://keybase.io/ff4500/key.asc
[twitter]: https://twitter.com/_xs
