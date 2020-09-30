# C4ptur3-th3-fl4g
A beginner level CTF challenge

## Translation and Shifting
1. c4n y0u c4p7u23 7h3 f149?
- Read the text and you'll understand.

2. ` 01101100 01100101 01110100 01110011 00100000 01110100 01110010 01111001 00100000 01110011 01101111 01101101 01100101 0010000001100010 01101001 01101110 01100001 01110010 01111001 00100000 01101111 01110101 01110100 00100001`
- Convert the binary to text

3. `MJQXGZJTGIQGS4ZAON2XAZLSEBRW63LNN5XCA2LOEBBVIRRHOM======`
- These are base32 encoding and can be decoded by running this command:
`echo 'MJQXGZJTGIQGS4ZAON2XAZLSEBRW63LNN5XCA2LOEBBVIRRHOM======' | base32 -d`

4. `RWFjaCBCYXNlNjQgZGlnaXQgcmVwcmVzZW50cyBleGFjdGx5IDYgYml0cyBvZiBkYXRhLg==`
- These are base64 encoding and can be decoded by running this command:
`echo 'RWFjaCBCYXNlNjQgZGlnaXQgcmVwcmVzZW50cyBleGFjdGx5IDYgYml0cyBvZiBkYXRhLg==' | base64 -d`

5. `68 65 78 61 64 65 63 69 6d 61 6c 20 6f 72 20 62 61 73 65 31 36 3f`
- Just lookup the ASCII table hexadecimal

6. `Ebgngr zr 13 cynprf!`
- ROT-13 encryption algorithm

7. `*@F DA:? >6 C:89E C@F?5 323J C:89E C@F?5 Wcf E:>6DX`
- ROT-47 encryption algorithm

8. `- . .-.. . -.-. --- -- -- ..- -. .. -.-. .- - .. --- -.
. -. -.-. --- -.. .. -. --.`
- Morse code

9. `85 110 112 97 99 107 32 116 104 105 115 32 66 67 68`
- Just lookup the ASCII table decimal

10. 
```
gLS0tLS0gLS0tLS0gLi0tLS0gLS0tLS0gLi0tLS0=....
.............................................
```
- This one is a little bit more tricky, because it combines multiple encoding. There are few good tool such as [CyberChef](https://gchqgithub.io/CyberChef/). You can create a decoding recipe one decoding block after another.

## Spectrograms
A spectrogram is a visual representation of the spectrum of frequencies of a signal as it varies with time. When applied to an audiosignal, spectrograms are sometimes called sonographs, voiceprints, or voicegrams. When the data is represented in a 3D plot they may becalled waterfalls. 

1.  Download the audio file. Use audacity to reveal the secret message

## Steganography
Steganography is the practice of concealing a file, message, image, or video within another file, message, image, or video.
1. Decode the image to reveal the answer. Use steghide
```
$ steghide --extract -sf stegosteg.jpg                                    
Enter passphrase: 
the file "steganopayload2248.txt" does already exist. overwrite ? (y/n) n
steghide: did not write to file "steganopayload2248.txt".

$ cat steganopayload2248.txt
```

## Security through Obscurity
Security through obscurity is the reliance in security engineering on the secrecy of the design or implementation as the main method ofproviding security for a system or component of a system.
1. Download and get 'inside' the file. What is the first filename & extension?
- Run this command `strings meme.jpg | tail -n 10`

2. Get inside the archive and inspect the file carefully. Find the hidden text.
- Same way as the first question.
