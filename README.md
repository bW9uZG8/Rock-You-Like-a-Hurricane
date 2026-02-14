# Rock-You-Like-a-Hurricane
Writeup on CTF challenge "Rock You Like a Hurricane" using the tools John the Ripper and pdf2john.

_This is my first writeup to test how to use GitHub and make writeups!_

<img width="498" height="325" alt="image" src="https://github.com/user-attachments/assets/abf25d3f-07c9-4a6f-8b11-9adb3c227172" />

This challenge states "We need to get this file open, but we forgot what we made the password. Can you help us out?" and includes a download for a PDF file. 

For this challenge I reccomend using the tools Kali Linux and John the Ripper, which are included within Kali Linux.


To start, I downloaded the file onto my Kali desktop to work with. Clicking on the file, you are prompted to enter a password which was not supplied.

<img width="631" height="293" alt="image" src="https://github.com/user-attachments/assets/923bd1e8-958d-400d-9c51-e960c4657e81" />

I went ahead and used "pdf2john" to extract the password hash of the PDF file and piped it into a text file that I named "Flaghash.txt". You can achieve this by making sure you are in the directory where the PDF file is located and typing "pdf2john Flag.pdf > Flaghash.txt" in your terminal to extract the password hash and create a file where the hash is located. 

<img width="508" height="223" alt="image" src="https://github.com/user-attachments/assets/03316a4f-f8e2-4241-9c92-ec60ff4b2f4c" />

With this hash, I could start the cracking proccess using the same tool, John. I decided to use one of the most common wordlists used in many CTF formats named "rockyou" which for me is located in /usr/share/wordlists/rockyou.txt. I also decided to use this wordlist because the name of the challenge is called, "Rock You Like a Hurricane", which hints at using the wordlist. Using the command "john Flaghash.txt --wordlist=/usr/share/wordlists/rockyou.txt" we could achieve this. 

<img width="787" height="237" alt="image" src="https://github.com/user-attachments/assets/57cbf590-2b6c-4c9a-87dc-2df7447a6b47" />

Success! We now have the password to the PDF file! If John did not prompt you with the password, you can use the flag "--show" to see it. "john Flaghash.txt --show" After copying and pasting the password into the PDF file, we have obtained the flag!

<img width="1919" height="965" alt="image" src="https://github.com/user-attachments/assets/37b03f4a-d255-43d2-a137-651513e659ff" />
