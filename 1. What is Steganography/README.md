# 1. What is Steganography?
Steganography is the practice of hiding secret messages in ordinary files or objects. The word itself comes from the Greek word steganos which means “hidden.”

Why is steganography important? Outside of being a fun CTF category, steganography allows messages to be hidden in plain sight and could be used to exfiltrate data by malicious actors or inject malware payloads (rare but possible). As aspiring students in cybersecurity, it is up to us to catch this! Whether it’s the invisible ink pen you used to trade notes with your friends in school, or a message hidden in an audio file in a jpeg, throughout this lesson, we are going to cover the tools of the trade so you too can discover these messages!

There are so many steganography techniques and ways to hide data, so this lesson will cover the most common CTF methods, 

### Exercise 1 - Hiding Your Own Text Messages
In order to understand the basics of Steganography, we are first going to use the tool Steghide. This tool allows us to hide data in various image and audio file types, as well as extract it.

Important commands:

`steghide info file`: Displays information about a file and whether it contains embedded data

`steghide embed -cf cvr.jpg -ef emb.txt`: Embeds the text file into the jpg file

`steghide extract -sf file`: Extracts embedded data from the file

Let's try it out!
1. Download a smallish .jpeg file of whatever you want
2. Create a .txt file with a *super secret message*
3. Use the embed command above to hide your text file in the image! (Leave the passphrase empty)
4. Check to make sure your data is successfully embedded using the info command
5. Partner up with another club member and post your images to the "Exercise 1.1" post in the "meeting-resources" channel in the main Discord
6. Take your partner's image and try to find the hidden data!

### Exercise 2 - Hiding Image Files Inside of Image Files
Using steghide again, see if you can hide your image containing a text file into another image! Then swap with a new or same partner again!

Congrats, you've now successfully learned how to hide very basic files and secretly send messages in plain sight!

### Challenge 1
See if you can slip a secret message into the Discord using the "memes" channel before next meeting. Bonus points if it's a picture of any pets you may have as your hidden message. Bonus bonus points if that hideen image contains a text file with their names :D
