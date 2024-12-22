# Identify and compare

The file provided to us has no extension, sending the file in a hex editor, the first two data types state BM, 
hence we were able to identify it as BMP file.

On opening the file it shows error. It's probably corrupted, so let's try comparing with a proper bmp fileto check what is wrong. online data is available showing
a proper table declaring all locations. Let's cross-reference using a hex editor that is visual studio.

Simply adjust the height, and correct the data in the header on the hex using the reference and save the file. The flag is visible on the Photo obtained

The flag is shown on the image.

**picoCTF{qu1t3_a_v13w_2020}**
