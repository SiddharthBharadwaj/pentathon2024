# Local bank returns

## Description

Welcome back to your uncle's bank, this time with a twist. The sensitive file is hidden deeper within intricate security measures and cunning traps. Can you rise to the challenge once again, navigating through heightened defenses to uncover the coveted secrets? It's time to put your skills to the test and prove your mastery of digital espionage.

PS: I heard that your uncle doesn't like nano text editor.

## Solution

1. By looking at the Nginx.conf file attached with the challenge, we get that we a LFI is possible if we craft the payload very carefully.
2. The challenge description also has a note which says "PS: I heard that your uncle doesn't like nano text editor." and the hint says "If it is not nano, then he might be using vim to edit html files". This suggests that the challenge has something to do with these text editors.
3. Turns out, these text editors create a swap (.swp) file of files being edited which can stay on the disk if not manually deleted.
4. Therefore our goal it to get the index.html.swp file.
5. The final payload including the url is: https://<id>.ch.eng.run/chall../chall/.index.html.swp
6. This will download the file in our system and the flag can be found inside

## Flag

flag{NginX_4li45_p4th_tr4v3r54l5_r_b4d!!!}