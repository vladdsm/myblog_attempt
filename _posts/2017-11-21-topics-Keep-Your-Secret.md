---
title: Cryptography is more fun with R!
excerpt: Use Public Key Cryptography with R Statistical Software [7 min read]
categories:
  - topics
date: 2017-11-21
author: vladdsm
background-image: Course_1387910_Revision_0_Designer_Sofía.png
tags:
  - non-programmer
  - openssl
  - tidyverse
  - Public Key Cryptography
  - Version Control
---

Cryptography is more fun with R!
--------------

**Cryptography** is usually percieved as something not for everybody in our society. It seems that majority just does not trust it. Probably due to these three things:

* *Conspiracy stories* - "...is there are *master key*?"
* *Not transparent* - "... what is happenning in this software?"
* *Too complex for me* - "... I need to be a programmer or mathematician to understand it!"

 **Takeaway \#1** : No transparency <-> No trust in society! 

At the same time **Cryptography** is really something that everyone need to know and use. *Simple password protection*, *food-chain traceability* or *Electronic Voting Systems* is something more people can benefit from. 

## Good news is that there is that **Public Key Cryptography** is easily available with **R Statistical Software**

This little article [7min read] aimes to illustrate that in just **10 lines of code**... More over you can easily see what is happening to learn, trust and finally benefit from this fascinating technology!

Public Key Cryptography and R Statistical Software
-----------------------

**Public Key Cryptography** is a type of Cryptographic system that uses set's of keys. They are known to be Public and Private. These keys are just numbers that can be used in combination with a fixed algorithm to Encrypt or Lock information and to Decrypt or Unlock information. We are not programmers to dig deep into algorithms however thanks to **R** we can look into the process itself. 

Encrypting popular phrase **'Hello World'** with `R`
----------------------

I will be using **R** packages **openssl** and **tidyverse** packages. Each package contains ready to use *Functions* that aimed to perform some manipulation with data. In case *function* generates an output we can use the `pipe|%>%` operator to pass this result to the next function. Packages can be downloaded from the internet for free and installed on your computer. Finally we are loading them for the further use

``` r
# Loading packages
library(openssl) 
library(tidyverse)
```

### Private Key

Private Key is generated from a large random number. Below 2 lines of code will generate the `Private Key` and write it as a file persistently. You can specify how 'long' your key should be. Just try to change the 'bits' number to see what happens. Another function will write the resulting private key to the file. We can use set a `password` to lock this file. This is optional, but highly recommended as it is required to 'unlock' private key number when you use it from file:

``` r
# generate your private key (NB: make sure to do back up copy!!!)
rsa_keygen(bits = 2099) %>% 
  write_pem(path = "my_key.pem", password = "")
```

## **You must make sure you have a valid copy of the Private key at any time.**

Thanks to `R` we can read this file back and see how this key is composed. Notice we use `str()` or structure function to do so:

``` r
# read private key from file and output structure of the object
read_key("my_key.pem",password = "") %>% str()
```

    ## List of 4
    ##  $ type  : chr "rsa"
    ##  $ size  : int 2099
    ##  $ pubkey:List of 5
    ##   ..$ type       : chr "rsa"
    ##   ..$ size       : int 2099
    ##   ..$ ssh        : chr "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABBwX/+M18K ..."
    ##   ..$ fingerprint:Classes 'hash', 'md5'  raw [1:16] 53 b8 cc f7 ...
    ##   ..$ data       :List of 2
    ##   .. ..$ e:Class 'bignum'  raw [1:3] 01 00 01
    ##   .. ..$ n:Class 'bignum'  raw [1:263] 05 ff f8 cd ...
    ##  $ data  :List of 8
    ##   ..$ e :Class 'bignum'  raw [1:3] 01 00 01
    ##   ..$ n :Class 'bignum'  raw [1:263] 05 ff f8 cd ...
    ##   ..$ p :Class 'bignum'  raw [1:132] 03 b9 f8 bf ...
    ##   ..$ q :Class 'bignum'  raw [1:132] 01 9c 2e 48 ...
    ##   ..$ d :Class 'bignum'  raw [1:263] 03 c5 01 b5 ...
    ##   ..$ dp:Class 'bignum'  raw [1:132] 01 c4 ba 56 ...
    ##   ..$ dq:Class 'bignum'  raw [1:132] 00 e6 8b d8 ...
    ##   ..$ qi:Class 'bignum'  raw [1:132] 00 db 2e 93 ...

Now try to spot that elements **e** and **n** are repeated. In fact the small portion of the numbers is duplicated and will be used in the **public key**

**Takeaway \#2** : `Private Key` contains `Public Key`

### Public Key

Public Key is consisting of a list of elements. Look above code output to have a glimpse. There we have a unique `metadata` of the key as well as a 'functional' part under the element `data`. These elements are used by the algorythm to **Encrypt** information. All we need now is to extract this element and store it to the file! We do so by reading the private key from the file, extracting public key and writing it to the separate file named `my_key.pub`. 

``` r
# generate your public key (NB: optional. Use Private Key to encrypt/decrypt)
read_key(file = "my_key.pem", password = "") %>% 
  # extract element of the list and write to file
  `[[`("pubkey") %>% write_pem("my_key.pub")
```

Here you go! Check out the file **my\_key.pub**. You can send it to your friends and they can encrypt information that you and only you can read... (if you have _*corresponding*_ private key of course!). But now we have our `keys`, now what?

### Encrypt with Public Key

Just as a simple example let's encrypt text "Hello World" and save this result as a file named `"message.enc"` :

``` r
## Encrypt with PUBLIC key file
"Hello World" %>% 
  # serialize the object
  serialize(connection = NULL) %>% 
  # encrypt the object
  encrypt_envelope("my_key.pub") %>% 
  # write encrypted data to File
  write_rds("message.enc")
```

Boom! It's already done, secret is encrypted however let's use `R` to see how it was possible...

Notice we were using function `serialize()` to transfer our data object to simple numbers. Lets see what exactly numbers...

``` r
## Encrypt with PUBLIC key (e.g. send this code to collaborator)
"Hello World" %>% 
  # serialize the object and output only 10 elements
  serialize(connection = NULL) %>% head(10)
```

    ##  [1] 58 0a 00 00 00 02 00 03 02 05

This vector of numbers can be encrypted with function `encrypt_envelope()`. This function is using our **public key** to encrypt our numbers:

``` r
"Hello World" %>% 
  # serialize the object
  serialize(connection = NULL) %>% 
  # encrypt the object
  encrypt_envelope("my_key.pub") %>% str()
```

    ## List of 3
    ##  $ iv     : raw [1:16] 76 b2 a8 3c ...
    ##  $ session: raw [1:263] 03 a3 a3 e2 ...
    ##  $ data   : raw [1:48] 48 27 53 0f ...

As a result we get a list of raw vectors which is already encrypted. However we just need to do a final step - store this object as a file. Function `write_rds()` can do it for us... 

### Read it back... decrypt

Decrypting this secret is almost opposite and probably does not need any comments. Just have a look on this chunk that does it for you:

``` r
# read file with Encrypted Information (from Computer File System to R Environment)
secret_encrypted <- read_rds("message.enc")

# decrypting the list from R Environment
decrypt_envelope(data = secret_encrypted$data,
                 iv = secret_encrypted$iv,
                 session = secret_encrypted$session,
                 key = "my_key.pem",
                 password = "") %>% 
  # getting back original object in a form of the data frame
  unserialize() 
```

    ## [1] "Hello World"

``` r
# remove secret_encrypted object
rm(secret_encrypted)
```

Finally we have our "Hello World" text back!


Conclusion
----------

Let's make some statistics and conclude this article:

| Operation  | Number of lines of code  |
|------------|--------------------------|
| keys       | 2                        |
| encrypt    | 4                        |
| decrypt    | 4                        |
| ---------- | ------------------------ |
| Total      | 10                       |

Of course `R` can not make micacles as we still don't know deep internals of encryption algorithms. However we now have much better understanding of it. More importantly we can use it on our own with just 10 lines of code.

RISKS and DISCLAMER
-----

**Cryptography** still should be used with caution. If you forget your email account password you may still restore it, but if you encrypt important business information and can not decrypt it... or if someone has got a copy of your private key... Unforgunate risks does exists so you may need to spend some time to practice your way using Public Key Cryptography on **Dummy** data...

DISCLAMER
------------
Code provided above is just for demostration purposes. There is a risk of loosing information. If you are using this code you do it on your own risk.

postscriptum
------------

beyong the theory I have also studied different simple ways to exploit this concept while doing everything possible to manage risks. The material is packed that to the e-learning course that will give you ready to use examples to exploit and use `Public Key Cryptography`. Remember that this course is created by *non-programmer* for *non-programmers*. Feel free to [check this out and benefit now!](https://www.udemy.com/keep-your-secrets-under-control/?couponCode=KEEP-SECRET-10)
