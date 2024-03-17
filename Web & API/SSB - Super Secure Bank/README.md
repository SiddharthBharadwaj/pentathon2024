# SSB - Super Secure Bank

## Description

Once upon a time, in a land far far away, there was a bank called Super Secure Bank. It was the most secure bank in the world. It was so secure that no one could ever hack it. But then, one day, a hacker came along and hacked it and encrypted all the data. Could you help the bank to recover the data and find the flag?

## Solution

1. This was actually a repeated challenge from 6 years ago (This information helped me alot)
2. Add a parameter p=XorIsNotSooS3cur3 to the URL (enc after decryption will give you p)
3. Final URL is https://<id>.ch.eng.run/?p=XorIsNotSooS3cur3
4. You will see the decoded flag at the bottom of the page

## Screenshots

![Image 1](images/image1.png)

## Flag

flag{586f7249734e6f74536f6f533363757233}