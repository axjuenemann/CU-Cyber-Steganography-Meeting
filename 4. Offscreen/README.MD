# 4. Offscreen
Hex editing is a big piece of steganography as at the end of the data, the hidden data is stored within the hex of the original file! However, hex editing can be powerful, especially when hiding a message in an image without actually embedding any new files into it! The `pngcheck` tool can be used to look for broken or corrupted chunks in a file, which can reveal sometimes if a png has been tampered with.

**Important Command:**

`pngcheck file`

One of the easiest ways to abuse the file format of a PNG is to edit the width or the height of the image to hide content that's still there, but can no longer be seen. For example, look at the below process:

As you can see, this image has very vital text that I wouldn't want the wrong hands to get ahold of, but my message channel has been tapped!

Knowing the PNG file format, I know that the width and height bytes occur after the IHDR bytes. Each gets 4 bytes respectively, and I can now shorten my image to crop out my hidden message for now. 

Oops, but now when using `pngcheck` I am getting an error that the CRC value is off. 

`CRC error in chunk IHDR (computed cd0dc2f8, expected 684fb6e4)`

By simply replacing the old CRC value with the expected one in the hex editor, this image is ready to send! 

### Exercise 1 - Cropped Out of My Life
1. Create an image with a message written on the bottom, and then crop that image out using hex editing! 
2. Partner up with another club member and post your images to the "Exercise 4.1" post in the "meeting-resources" channel in the main Discord
3. Take your partner's image and undo the crop!

### Exercise 2 - Princess (DeadFace 2024)
Rumor has it this image of Princess used to have a dog bowl in it... what is the flag?

### Challenge 2 - Look the Other Way
We just intercepted what we believe to be very malicious actors sending a png file. Other tools fail to indicate that anything is hidden in this, but can you find something, it looks unnatural? We think the width may be off by a value of 1... (Use the challenge.png file)
