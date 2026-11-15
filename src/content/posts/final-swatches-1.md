---
title: 'Final Swatches #1'
date: 2026-11-09T16:51:00
summary: For my final project, I am working with thermochromics and testing different weaving patterns and heating techniques to achieve programmable, color shifting designs. For the first round of swatches, I experimented with using resistive thread as a heating element, threaded along the inside of a strand of thermochromic warp yarn. I set up the loom by splitting the warp up into 5 sections, alternating between regular and heated yarn. This essentially made two different circuits, separated and sandwiched between insulated sections. I would then weave 1-2 inch sections using different techniques (mostly tabby, varying the yarn colors), so that I could see different effects in the heated sections created by variation in color and pattern.
cover: /uploads/Screenshot 2026-11-14 at 4.51.21 PM.png
draft: false
status: in-progress
blocks:
  - type: heading
    text: Materials, Process, and Planning
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
---
