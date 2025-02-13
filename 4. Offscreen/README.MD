# 4. Offscreen
One really sneaky trick that some CTFs may try is editing the dimension parameters of the image itself to force most common image viewers to ignore certain parts of the image. In spite of how simple all of this sounds, there was a hard challenge like this in NCL that stumped a lot of people the season it got introduced - simply because most steganography tools don't care about something so seemingly basic. For an example, look at the below process:

As you can see, this image has very vital text that I wouldn't want the wrong hands to get ahold of, but my message channel has been tapped!

![image](https://github.com/user-attachments/assets/98aed681-7736-43b8-a6bd-b72aaed2beb4)

Knowing the PNG file format, I know that the width and height bytes occur after the IHDR bytes. Each gets 4 bytes respectively, and I can now shorten my image to crop out my hidden message for now.

![Screenshot 2025-02-12 155404](https://github.com/user-attachments/assets/2e34d87f-a6c1-4c10-b139-023ae6bc8300)

There's more to consider, however. The PNG file format includes checksums at the end of each chunk that serves as a sort of "verification" that the chunk hasn't been corrupted in some way. We can examine the integrity of a PNG through these checksums using the `pngcheck` tool.

**Important Command:** `pngcheck file`

Oops! When using `pngcheck` on our tampered image, we get an error that the CRC (checksum) value is off:

`CRC error in chunk IHDR (computed cd0dc2f8, expected 684fb6e4)`

It seems that our tampering triggered the PNG's built-in corruption check. Luckily, this is easily bypassable. By simply replacing the old CRC value with the expected one in the hex editor, this image is ready to send!

![rick](https://github.com/user-attachments/assets/736f630f-70d9-4ffe-9fe1-a0736c17044e)

### Exercise 1 - Cropped Out of My Life
1. Create an image with a message written on the bottom, and then crop that image out using hex editing! 
2. Partner up with another club member and post your images to the "Exercise 4.1" post in the "meeting-resources" channel in the main Discord
3. Take your partner's image and undo the crop!

### Challenge 1 - Princess (DeadFace 2024)
Rumor has it this image of Princess used to have a dog bowl in it... what is the flag? (use princess.png)

### Challenge 2 - Look the Other Way
We just intercepted what we believe to be very malicious actors sending a png file. Other tools fail to indicate that anything is hidden in this, but can you find something, it looks unnatural? We think the width may be off by a value of 1... (use the challenge.png file)

### Challenge 3 - Worldview (Original, but based off an NCL challenge some years back)
But this one's a jpg? (use Worldview.jpg)

<details>
	<summary>Solution:</summary>
	
	<p>The general principle is the same - but now you must research the JPG format instead.</p>
	<ol>
		<li>Upload the image into CyberChef. You can drag and drop it or use the "open file as input" button in the top right corner. Then drop "To Hex" into your recipe.</li>
		<li>Copy and paste the output into a text file.</li>
		<li>Search for the hex string "ff c0". This set of bytes denotes the JPEG marker (https://en.wikipedia.org/wiki/JPEG#Syntax_and_structure) SOF0, which includes width and height information.</li>
		<li>You should see a string of bytes that looks like "ff c0 00 11 08 00 af 00 64". Of these bytes, change "af" (175 in decimal) to "ff" (255). In other words, that string of bytes should now read "ff c0 00 11 08 00 ff 00 64". This changes the width from 175 to 255.</li>
		<li>Select the entire text file (ctrl+a) and copy+paste all of it into a new CyberChef window. Put "from hex" and then "render image" into the recipe.</li>
		<li>Tadaaaaaa! :)</li>
	</ol>
</details>