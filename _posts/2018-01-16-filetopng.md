---
layout: post
title: FileToPNG
tags: computer-science
---
## What is FileToPNG?
FileToPNG is a tool written in Java that converts the raw bit representation of any file into a corresponding PNG representation. The PNG (being a lossless file type) can be sent (via text, email, etc) and finally reconstructed back into a file. The GithHub repository for this project can be found [here](https://github.com/ozanerhansha/FileToPNG).

That said, while the main purpose of FileToPNG was to make a tool for sending files over image only communication channels, I've found that the PNG representation of the files have interesting properties based on what kind of files are put in.

<!--more-->

## The Main Algorithm
While I have programmed a primitive UI (the code for which can be found [here](https://github.com/ozanerhansha/FileToPNG/blob/master/src/Main.java)) to make using the tool easier, it's not the main focus of FileToPNG and is really just boilerplate Java.

The real meat of the program is the conversion functions for PNG to File and vice versa. The code for this can be found [here](https://github.com/ozanerhansha/FileToPNG/blob/master/src/GFile.java)

The algorithm goes something like this:
1. Convert the file into a string of bytes (8 bits = 1 byte).
2. Read through this list and make a pixel out of every 3 bytes. This can be done because a pixel is comprised of 3 colors (red, green, and blue) each with a value from 0-255. These 256 values can be represented in 8 bits (because 2<sup>8</sup>=256).
4. Once a list of pixels (which should be about a 1/3 of the size of the byte list) has been made, create a square image (in .png format) out of these pixels.
5. Account for files whose bytes aren't a multiple of 3. (I used special '2 byte' and '1 byte' pixels that have different alpha values to demarcate them)

Reconstructing the images into files is as simple as reversing this process.

## Properties of PNG Representations
The main algorithm doesn't do any encrypting (as of yet) or rearranging of the file's bits. As such, the PNG representation of the file can give us an, obfuscated to be sure, look at its structure.

### Text Files
Take text files for example. Their content, of course, varies widely depending on the length and topic of discussion. But, even if they don't use the same language, they all still use the same Unicode characters which all have the same configuration of bits. Meaning they share some similarities:

![Text in FileToPNG](/assets/projects/filetopng/text_diagram.png?style=centerme)

### 1MB file of random noise for comparison:
![Random Noise](/assets/projects/filetopng/random_data.png?style=centerme){:width="500px"}

### Music Files
This one was kind of surprising. When I took an .mp3 file of a song and put it through the program, the resulting image looked almost random:

![mp3](/assets/projects/filetopng/song_mp3.png?style=centerme){:width="500px"}

I was disappointed at first, but then I realized that randomness is fundamentally information packed. What I mean is that if the PNG representation had some sort of overarching structure, then that would imply that there is still some redundancy in the file that could be compressed, thereby making the file smaller and more random looking.

This lines up with the fact that mp3 files are **lossy** (i.e they sacrifice perfect quality for a smaller size).

![wav](/assets/projects/filetopng/song_wav.png?style=centerme){:width="500px"}

The natural step forward at that point was to get a .wav version of the song (which is **lossless**) and see if it had any structure. And as expected, it did. It was also much bigger in size due to being lossless (the size difference isn't reflected here because it would extend out of the webpage).

### Nintendo 64 ROMs
As a test I thought I would try converting a couple of Nintendo 64 games (in file form) that were on my desktop to PNGs and, unsurprisingly, they share many similarities:

![N64 Roms in FileToPNG](/assets/projects/filetopng/n64_diagram.png?style=centerme)

Interested, I did some research into N64 cartridges and found out that all 'ROM dumps' (files that were created by copying a physical N64 cartridge onto a computer) have what's called a *header*. This header includes custodial information like the game's version, internal name, and other bits of information that would be interesting to a game historian. This header is the black box at the top *Super Mario 64* and *Mario Kart 64*.

You may also notice that Super Mario 64 is smaller than Mario Kart 64, implying that it has a smaller file size. Apparently, N64 games came on a variety of hardware with different storage capacities and capabilities. This may seem normal nowadays but in an era where all games had to work on the same piece of limited hardware, this variability is pretty amazing.

Anyway this is also reflected at the bottom of the PNG representations. After the last black bar, both the ROMs are just filled with 'garbage data' meant to fill the ROM up. You can tell because this section looks more like the random sample then the rest of the picture.
