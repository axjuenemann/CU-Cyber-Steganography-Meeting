# 2. Metadata
Metadata is data that describes other data. For example, if you take a picture on your phone, that photo has tons of metadata, including when it was taken, where it was taken, and what model of camera took it!

Conveniently, we can edit this data to hide our own messages!

The tool of choice for viewing this metadata is `exiftool`

**Important Commands:**

`exiftool file`: shows metadata of the passed in file

### Exercise 1 - Oh no Clippy! (Deadface CTF 2024)
Use the metadata in the image to find out why Clippy is so angry! (Use angry-clippy.jpeg)

<details>
  <summary>Solution:</summary>
  <p>Clippy hates his job! By running exiftool, you should see the following metadata:
    
  https://github.com/user-attachments/assets/8f76c4de-c049-45a4-9b1f-9a873357d192
  
  Fun side note about this challenge is that it was originally used to find the website in the metadata that then lead to a web exploitation challenge
</p>

</details>

### Exercise 2 - Isn't This Just Beatiful? (StegOnline)
Can you find the flag in the metadata? (Use file exif-stego.jpg)

<details>
  <summary>Solution:</summary>
  <p>By running exiftool, you should see the following flag in the metadata:
    flag{3x1f_i5_c00l}
</p>

</details>

