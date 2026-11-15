---
title: 'Final Swatches #1'
date: 2026-11-09T16:51:00
summary: For my final project, I am working with thermochromics and testing different weaving patterns and heating techniques to achieve programmable, color shifting designs. For the first round of swatches, I experimented with using resistive thread as a heating element, threaded along the inside of a strand of thermochromic warp yarn. I set up the loom by splitting the warp up into 5 sections, alternating between regular and heated yarn. This essentially made two different circuits, separated and sandwiched between insulated sections. I would then weave 1-2 inch sections using different techniques (mostly tabby, varying the yarn colors), so that I could see different effects in the heated sections created by variation in color and pattern.
cover: /uploads/Screenshot 2026-11-14 at 4.51.21 PM.png
draft: false
status: in-progress
blocks:
  - type: heading
    text: 'Process Journal: Materials, Process, and Planning'
  - type: paragraph
    body: |-
      Materials:
      \- Thermochromic Yarn (the yarn i used: [amazon link to yarn](https://www.amazon.com/Sensitive-Changing-Temperature-Crocheting-Beginners/dp/B0G39HXS92?pd_rd_w=droQH&content-id=amzn1.sym.067cfcd5-045b-45a5-8758-4a4c89764364&pf_rd_p=067cfcd5-045b-45a5-8758-4a4c89764364&pf_rd_r=4GVDDQ6BK4K3V63JST53&pd_rd_wg=kD5oF&pd_rd_r=673f5502-1e8f-40e9-8a7c-5dda2dae48b8&pd_rd_i=B0G39HXS92&ref_=pd_bap_d_grid_rp_cbr_0_1_ec_pr_t&th=1))
      \- ESP32 (this project uses an ESP32-S3, but any microcontroller compatible with Arduino IDE will do)
      \- Regular, non thermochromic yarn
      \- Resistive thread (measure length of heating element thread and figure out the total resistance of your thread)
      \- Loom (make sure you can remove the fabric from whatever loom you are using without cutting the warp threads)
      \- jumper wire
      \- alligator clips
      \- multimeter
      \- IRLZ44N MOSFET transistor
      \- 10k ohm resistor, resistors between 100-300 ohms
      \- copper tape

      Process: 
      1\. use a sewing needle to thread resistive thread through the center of about 24 inches of thermochromic yarn. Repeat for a second circuit.
      2\. Seal each end of the conductive color changing yarn with a piece of copper tape.
      3\. Warp the loom in 5 separate sections using 5 pieces of yarn around 24 inches long (or whatever length needed to fit loom size), wrapping each piece of yarn around the loom 4 times to create 4 warps per section (20 warps total). This setup can be adjusted depending on how big your loom is/how big your desired sample is/how many warp circuits you create, but the effect created in this experiment relies on alternating between heated and non-heated warp sections. For this setup specifically, turning both heating elements on creates two color-shifting stripes about 1 inch in width running vertically on the cloth, with the vertical stripe only visible when heated.
      4\. weave your little heart out, try making 1-2 inch sections using different techniques to see how these vary when heated. then secure your wefts at the end. keep swatch on loom or remove swatch without cutting the circuits warps; if you have to cut warps, make sure to reconnect your circuits where appropriate before connecting to power source.
      5\. Connect the ends of the circuit warps to a power source. There are multiple ways to do this, if you want to program the circuits to switch on and off, use a transistor instead of directly connecting heating thread ends to microcontroller/power source.

      Planning:
      this resource is a great guide for working with thermochromics and includes a section with circuit diagrams:
      [https://unstable.design/books/prototyping-experimental-textiles/docs/lessons/thermochromics/](https://unstable.design/books/prototyping-experimental-textiles/docs/lessons/thermochromics/)


      I wanted to create an experiment that was simple, but still allowed me multiple testing possibilities. I planned to warp the loom in 5 sections, alternating between regular and heated yarn, so that I could test two different circuits. I had two different threads I could use for a heating element, so one of the circuits uses copper thread, the other uses stainless steel thread (or silver, I actually don't know what the material is). For the actual weaving part, I didn't plan this out too much and freestyled pretty much the whole way, alternating between different colors of thermochromic yarn and regular yarn. I mainly stuck with plain tabby, but I tried to do some twill-like patterns toward the end. The goal behind this experiment was to test variation in heating and what this looks like with different patterns woven in between the heating elements, so I tried a new technique each time I switched the weft color. The other part of planning was wiring the heating element. My goal was just to make a breadboard prototype, later I will worry about making the swatch freestanding with a connected power source, but first I needed to create a working, programmable circuit. 

      The first thing I tried was connecting each end of the wire to a 9V battery's positive and negative terminals. reminder: DO NOT DO THIS, I almost started a fire. To do this safely, calculate the resistance needed (based on your power source and thread resistance),  connect your thread ends to jumper wire or connector clips, add desired amount of resistance and wire this up on a breadboard with your power source and microcontroller. If you want this to be even safer and better, use a MOSFET transistor in your circuit. A npn 2222 could also work here, but I only made this work once and never again, the npn 2222 doesn't draw enough current for my heating elements.

      I wrote a simple arduino script to flash to my esp32 development board that controls the connected heating element by turning it on for a few seconds, and off for a few seconds.
  - type: code
    language: cpp
    filename: arduino script for switching on/off a single connected warp circuit
    code: |-
      const int HEATER_PIN = 4;

      void setup() {
      Serial.begin(115200);
      pinMode(HEATER_PIN, OUTPUT);
      digitalWrite(HEATER_PIN, LOW);
      delay(2000);
      }

      void loop() {
        Serial.println("heater on");
        digitalWrite(HEATER_PIN, HIGH);
        delay(10000);

        Serial.print("heater off");
        digitalWrite(HEATER_PIN, LOW);
        delay(3000);
      }
  - type: photo
    image: /uploads/9F0B597A-F285-4066-A67F-3860A4CAB93F_1_105_c.jpeg
    alt: embedding copper thread into thermochromic yarn with a sewing needle
    caption: 'embedding copper thread into thermochromic yarn: using a sewing needle to feed the resistive thread through color-changing yarn'
    width: normal
  - type: photo
    image: /uploads/3ACFCF59-5587-41F0-890B-A6C7C488A5E2_1_105_c.jpeg
    alt: thermochromic warp thread embedded with resistive thread, copper tape for connection points
    caption: thermochromic warp thread embedded with resistive thread, copper tape for connection points
    width: normal
  - type: photo
    image: /uploads/78D39B8F-CC41-4E4D-8B4E-39487B0F71A8_4_5005_c.jpeg
    alt: loom warped in 5 sections, using an embroidery machine hoop as loom
    caption: warp the loom in separate sections, this weave is using an embroidery machine hoop as the loom
    width: normal
  - type: photo
    image: /uploads/FFFBFDAC-3B59-4CCF-892E-C17FF3BCAB91_1_105_c.jpeg
    alt: swatch after weaving
    caption: swatch after weaving, orange = thermochromic (yellow), gray = thermochromic (pink), navy/light blue don't change color
    width: normal
  - type: photo
    image: /uploads/53A95918-77D2-44DE-9AA9-0FA262A5441A_1_105_c.jpeg
    alt: finished swatch activated by body heat
    caption: finished swatch activated by body heat. color change can also be activated by breath, though this is not as controlled.
    width: normal
  - type: heading
    text: 'Process Journal: debugging a swatch'
  - type: paragraph
    body: |-
      I thought I had a solid understanding of how to set up this circuit, but I ran into so many issues in the process of getting the resistive thread to heat up. It was challenging to get a solid connection to the thread, do the right calculations, and determine where the circuit was failing. Usually the problems I run into when programming circuits are issues in the code, but this project required me to do a lot of physical debugging by testing different connection points with a multimeter. 
      I first set up my circuit by connecting GPIO 4 on my ESP32 to the base of the npn 2222 with a 220 ohm resistor. Using the 5v pin as my power source, I connected that the breadboard power rail, and one of the ESP's GND pins connected to the negative side of the power rail. The base of the transistor is also connected to the ground rail with a 10k ohm resistor. The transistor's collector leg is connected to one end of the resistive thread, with the other end of the resistive thread connected to the power rail. Then, connect the transistor's emitter to GND. 
      At first, I thought this circuit was working, because it started heating up the swatch when I ran the code. Then I realized that I had one or two connections out of place, and somehow it was completing the circuit without the transistor, so it was not allowing the heating element to switch between on/off states. 
      When I connected it correctly as described above, it did not work anymore, and this sent me down a rabbit hole. I connected the multimeter to each connection point in the circuit to make sure everything was connected and the voltage was moving through the heating element. It seemingly passed every test, but after burning out 3 transistors, 2 batteries, and 1 small fire, I concluded that something was wrong. My best solution for now is: new components. I did a bit more research and ordered some IRLZ44N transistors to replace the npn2222.
  - type: youtube
    caption: I got it to work...kinda
    url: https://youtu.be/S-EUHuFT3QU
  - type: heading
    text: 'Process Journal: Perseverance'
  - type: paragraph
    body: |-
      I became determined to make this work. I had tried so many different batteries, resistors, microcontrollers, and 2 different types of thread. 
      My ideal result would be switching the heating element on and off in timed intervals to fade between colors, then connecting both heating elements to the microcontroller to alternate between the two. For now, at least I know what it looks like when the heat is on and in between states as it heats and cools. Note: takes \~30-90 sec for the color to fully shift, longer for cool down. 
      It would be ideal to have more control over the heating thread. Instead of having the timer switch on/off after so many seconds, I adjusted my arduino script to use buttons to turn the heater on/off, also adding a button to adjust the power level. I used an arduino graphics library to make a simple interface for my esp32 microcontroller. I could've just used my computer keys and my terminal, but I had to use the esp32's usbc port for a power bank since the 9V battery wasn't working, so I could no longer use terminal/serial monitor while turning heat on/off. See video below to see how this setup works.
---
