---
title: 'Final Swatches #2'
date: 2026-11-20T08:45:00
summary: For my second round of swatches, I wanted to experiment with a new technique and connect multiple heating elements now that I had figured out the wiring. Instead of using the warp threads as heating elements, I wanted to hide the heating threads inside weft threads. I wanted the final product to be a plain, single colored swatch that reveals an invisible design when heated. The biggest challenge with this is that the yarn with the embedded heating element looked exactly like the regular yarn, so I kept having to make sure I was using the right weft.
cover: /uploads/0AD7114B-8E6C-4208-93D3-078622522B29_4_5005_c.jpeg
draft: false
status: completed
blocks:
  - type: heading
    text: Setting Up
  - type: paragraph
    body: |-
      Materials:
      \- orange to yellow thermochromic yarn
      \- gray to pink thermochromic yarn
      \- stainless steel conductive thread \~ 10 ohms per foot
      \- copper tape
      \- alligator clips
      \- loom (I used an embroidery hoop)
      \- shuttle (I used a sewing needle, popsicle sticks, and q-tips, also a flosser at one point)
      \- jumper wire
      \- esp32
      \- power source with 5V output, needs to be able to give up to 2A current
      \- IRLZ44N MOSFET transistor
      \- 220 Ohm resistor and 10k ohm resistor
      \- jumper wire
      \- breadboard 
      \- laptop with arduino IDE installed

      Before weaving, it is important to prep the heating yarn. I fed some stainless steel thread through a long piece of yarn, then cut off 6-8 inch pieces as I needed them. The resistance is pretty high for my power source so the thread can't be too long. I made a plan of how I wanted to weave this. I wanted it to be sort of a checkered pattern with alternating stripes on each side. I would weave a few rows of tabby with the regular yarn, then one half row with the heater yarn, a couple more rows of regular tabby, then another row of heated yarn. After each half-width stripe, I'd do about 5 more rows of tabby then do the same process on the other side. I tested this out with the first stripe and the method of doing two regular yarns in between two heater yarns worked really well (see above photo). 

      \*\* Unfortunately, I was not able to test this out again because my esp32 board broke. Will update this post with pictures of the heat activated swatches when the new esp arrives \*\* 

      I wanted to make the transition between the two yarns as seamless as possible so that you wouldn't be able to tell what the image was until it was heat activated (or that an image was even there). This was very successful in my first swatch, but when I weaved a message into the second swatch, it did not look as clean. See pictures below for demonstration on how to weave together the two different yarns:
  - type: photo
    image: /uploads/397E1CB7-C4A2-4AD8-8CA8-6E5A8C48C74C_4_5005_c.jpeg
    alt: weaving together two types of yarn
    caption: weaving together two types of yarn
    width: normal
  - type: photo
    image: /uploads/8FA0B905-F29F-4C06-9A18-23BDF7914140_4_5005_c.jpeg
    alt: weaving together two types of yarn
    caption: weaving together two types of yarn
    width: normal
  - type: photo
    image: /uploads/5A30A713-DCDA-4A3C-8E79-3F9064D7FB13_4_5005_c.jpeg
    alt: weaving together two types of yarn
    caption: weaving together two types of yarn
    width: normal
  - type: heading
    text: Second Swatch
  - type: paragraph
    body: For this swatch I wanted to write some kind of hidden message. I decided to start with an easy 2 letter word like "Hi". Was going to do "Ok" but weaving those shapes was a lot more complicated. Since it was hard to keep track of two different yarns that look exactly the same, I first wove the outline of the word and then wove in the regular yarn.
  - type: photo
    image: /uploads/58F6E07E-9D2C-40BE-B431-C2C4773A83EA_4_5005_c.jpeg
    alt: weaving a word
    caption: weaving a word
    width: normal
  - type: paragraph
    body: |-
      I made the weave with the conductive yarn pretty sparse so the conductive thread wouldn't touch, my plan was to weave the regular yarn in between the conductive rows for extra insulation. 

      In hindsight this may have not been the best strategy, next time I will draw out my plan first and weave from bottom to top row by row instead of filling in the gaps later. Another easier way of doing this would be to weave in the conductive thread LAST into the shape I want. I've thought about doing this but want the shape to be as discrete as possible, only visible when the conductive thread is heated. 

      Another idea that I have is getting an identical yarn that is not thermochromic and using this for my "regular yarn". If I did it this way, the resistive thread would not even be needed, the shape would be invisible until heat activated, and the heat activation could come from anywhere (body heat, etc) and only shift the color in the desired areas. This would be ideal for regions that only have two color states, but if you want a section to have more than one color change possibility, embedding and layering the resistive thread could allow you to make different designs in the same region. 

      The experiments I've done so far have only had two states, so it would have been much easier to weave in the conductive thread or use a similar, non-thermochromic gray thread in place of my "regular" yarn, but I wanted to test how well the thread would be insulated/hidden inside of a piece of yarn. This actually worked great for the first section, as the pattern was more simple and I did it row by row instead of filling in gaps. 

      My second swatch with the hidden message "hi" didn't look as good when finished. It was difficult to fill in gaps and make everything even in the end, so the weave was a bit more disorganized and sparse, but the message was still hidden pretty well. See photo below to compare swatches (not heat activated).
  - type: photo
    image: /uploads/IMG_3637.jpeg
    alt: finished swatches
    caption: 'finished swatches: top = hidden message "hi" ; bottom = hidden colorblock'
    width: normal
  - type: heading
    text: Taking swatches off the loom
  - type: paragraph
    body: |-
      Since the yarn was so thin, and the resistive thread needed to be short, I made these swatches pretty small. I cut the fabric off the loom, tied the warp ends to secure everything, then cut the piece in half in between the two sections. I sealed the other sides with glue so that I didn't have to take off any  more height or risk shifting the resistive threads. I then secured both ends of each thread to alligator clips so I had an easy way to attach them to jumper wires. 

      The hidden colorblock swatch has a total of 5 heating elements, and would have to connect to 10 jumper wires. I am still working on getting this all connected. 

      The hidden message swatch has a total of 2 heating elements, the "H" is one path, the "I" is another path, and each path has 2 ends, so it would need to connect to 4 jumper wires. 

      Since I cut the resistive thread short, I could probably connect two heating paths to one jumper wire or put two heating paths in series. I unfortunately have not been able to test this as my esp32 broke (from unrelated causes). I have ran into a setback as I try to wire up a new setup with a different esp32 and separate OLED screen (see below):
  - type: photo
    image: /uploads/IMG_3641.jpeg
    alt: new wiring setup
    caption: new temporary wiring setup (incomplete) using 0.96 inch OLED display and basic ESP32 dev module
    width: normal
  - type: heading
    text: Work in progress
  - type: paragraph
    body: |-
      I really tried to prioritize getting this assignment in on a timely manner, but could not get the circuit to work in time. After taking an extra day to try and complete it, I unfortunately still was unsuccessful, and have ran into some complications getting the temporary wiring set up. I am continuing to troubleshoot this over the weekend and will update with photos when I get it working. I ordered a new development board with an attached screen, so that will work with the remote control program that I currently have working, and then I can continue testing.

      My goal over the next week is to make the wiring and electrical components more incorporated into the design, or at least more compact. With the next round of swatches I make, I'd ideally like to make a pocket for the microcontroller and battery pack, and figure out a way to make the circuit a part of the weave.
  - type: heading
    text: Planning Next Steps
  - type: paragraph
    body: |-
      Now that I have a good understanding of how I want to incorporate heating elements, how to set up the circuit, and the types of designs I want to make, I am ready to start making this on the big looms at school. This will significantly speed up the weaving process, especially having the patterns planned out. The first round of swatches was just for freestyling, experimenting, and getting comfortable with incorporating circuits into fabric. The second round (this assignment) was all about polishing my technique and using the information I had gathered from the first round to inform my process. I also prepared a big bundle of my diy conductive yarn so that I have this ready to bring to the loom. 

      My next steps are to get a non-thermochromic yarn identical to the orange and gray thermochromic yarns that I have. This will be easier to create the hidden message design with and I plan to make at least one swatch like this with just the two contrasting yarns and no embedded heating circuit. 

      My biggest goal for my final round of swatches is to create a swatch that is programmable, meaning it can display multiple different images/shapes in the same region of the fabric. One idea that I have is weaving in a happy face shaped circuit on top of a sad face shaped circuit, both invisible until heated. Depending on which button you press with the remote control, either a smiley face or sad face will appear. 

      Another idea I have is weaving a track of paw prints, pressing a button will make the color shift in sequence from left to right as if something is walking across the fabric. 

      My stretch goal is making the electronic components as sleek and compact as possible. The main thing I want to experiment is the capabilities of thermochromics, but to actually incorporate this into a real product, the electronics have to be seamlessly incorporated. I want to make at least one swatch that considers the electronics in the design, whether that is a pocket, or a 3d printed enclosure for the electrical components, but either way I will likely have to do some soldering.
---
