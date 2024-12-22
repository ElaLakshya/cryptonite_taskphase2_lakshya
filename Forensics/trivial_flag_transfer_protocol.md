# Changing data with photos.

For this program asks us to find out the path of the traffic, we will use a tool such
as wireshark to analyse the traffic.

We open the file in wireshark and we can see a lot of things going on. we can export the data
in tftp format and save all files in our folders.

We can now see an instructions.txt, plan, and 3 images. 

Exploring the program.deb file we can notice the steghide program.This hints that 
the data will be stored within one of the images.

The instructions.txt and plan file both are encrypted, on analysis, they turn out to be rot and when
changed to ascii give out instructions and leak the password used to hide the data in the images.

Let's run these files

```stegide extract -sf picture1.bmp```

On running on all three files, we get our flag.

```
root@TurboMachine:~/challenge# steghide extract -sf picture1.bmp
Enter passphrase:
steghide: could not extract any data with that passphrase!
root@TurboMachine:~/challenge# steghide extract -sf picture2.bmp
Enter passphrase:
steghide: could not extract any data with that passphrase!
root@TurboMachine:~/challenge# steghide extract -sf picture3.bmp
Enter passphrase:
wrote extracted data to "flag.txt".
root@TurboMachine:~/challenge# ls
flag.txt  instructions.txt  picture1.bmp  picture2.bmp  picture3.bmp  plan  program.deb
root@TurboMachine:~/challenge# cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
root@TurboMachine:~/challenge#
```

**picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}**
