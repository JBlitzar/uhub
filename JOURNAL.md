# 5/9/2026 8 PM - Researched, made prelim schematic, routed it

_Time spent: 2.883333333333333h_

first journal!!

So I got my idea, which is to make a USB hub. this is useful both for my computer and for the raspberry pi I own, I have lots of usb accessories and this would consolidate ports. To spice things up, I'm daisy-chaining two ICs together. I found a guide that goes through the general steps, but obviously I'm doing my own thing since, you know, I'm using two ICs, using easyeda instead of kicad, and doing it myself.

I got all the footprints imported, and that worked great. I worked on the schematic, and asked for feedback on slack. Everything was correct except I mistook the sbu lines for the cc lines.

Routing's kind of nightmarish because all the data lines need to have no vias, need to be approximately length matched in the differential pairs, and are all on one layer. In the end, I got it done! I am quite proud of my routing. All in just two layers. :)

Only DRC errors after I connected everything were not my fault--corrupted footprints, although hopefully in review they can make sure it's all good.

Anyways, yeah!
![Screenshot 2026-05-09 at 8.28.07 PM](https://stasis.hackclub-assets.com/images/1778383691057-e1lfk9.png)

![image](https://stasis.hackclub-assets.com/images/1778383709329-y1hyff.png)

![Screenshot 2026-05-09 at 8.28.47 PM](https://stasis.hackclub-assets.com/images/1778383731022-jzmocs.png)

# 5/10/2026 9 AM - Made all the traces good

_Time spent: 0.5833333333333334h_

More wiggly traces, should be length-matched and no big distance changes between differential pairs.

I also cleaned up the silkscreen

But mostly I was just fiddling around in kicad. I guess I cleaned up the ground plane. The board itself's mostly done (?) so project work time after this'll probably be making it shipped, and debugging

![Screenshot 2026-05-10 at 8.41.43 AM](https://stasis.hackclub-assets.com/images/1778427721820-uhkntk.png)

# 5/10/2026 3 PM - Cadded case, wrote docs, reviewed guidelines

_Time spent: 2h_

I went through all the requirements. I also made a nice case in onshape :)

Now, my repo is properly organized, and the readme walks readers through what the project is. I also made some super cool 3D renders in blender!!

![image](https://stasis.hackclub-assets.com/images/1778451918757-ozgwla.png)

![Screenshot 2026-05-10 at 3.23.11 PM](https://stasis.hackclub-assets.com/images/1778451796360-aiy1ze.png)

# 5/26/2026 5 PM - Migrated to Forge, added mounting holes, etc

_Time spent: 1.43h_

Stasis review was stagnant for two weeks, I guess the reviewers are busy. I've decided to migrate to Forge. Most of the stuff just copied over. I then did some research about BOM reduction, but I genuinely can't because of the special IC is in the extended parts. It's not too bad anyways, can always pay out of the other grant if I really have to.

I also added mounting holes. I couldn't go for the standard all-four-corners layout because my PCB's pretty packed, but top left corner and bottom middle should be good enough. It's just for securing things in the case. I then added the holes to the case. The plan is to use M3 screws and have a mangement system similar to the Hackpad, where there's a 6mm hole at the bottom to fit the head of the screw, then a 3mm hole in the pcb. This also nicely elevates it from the surface, which is kind of cool. Then the nut will just be screwed in from the top and visible, so just a 3mm hole on the top of the case. No BOM additions needed since I'll just self-source these m3 screws and nuts.

The fact that some traces are inside the courtyard shouldn't be a problem (no 3d components or anything, plus the back, where the screw head's actually going to be, is completely clear). Then again, I'm no pcb expert.

I re-exported twice because I at first did 5mm instead of 6mm for the m3 head, and then I wanted to nitpick some traces.

All this combined genuinely took an hour and a half: I timed when I started. Anyways, there you go.

![](https://cdn.hackclub.com/019e66c7-c60d-7169-b0b7-23d2ae303248/Screenshot%202026-05-26%20at%205.13.43%E2%80%AFPM.png)

![](https://cdn.hackclub.com/019e66ca-15ee-7864-91b7-fefe85431215/Screenshot%202026-05-26%20at%205.16.12%E2%80%AFPM.png)


# 6/3/2026 7 PM - Most traumatic session ordering JLC

_Time spent: 0.1h_

> This took more like 0.5-1 hours, but this of course doesn't count as hardware learning time, so I'm deflating myself here. 

Anyways, I went to upload all my stuff to JLC. And I was clicking through, selecting my various things. Then it's time for PCBA. Now keep in mind
I've never done pcba before, so it was pretty new to me. I uploaded my bom and uploaded my positions csv. One small hiccup that my hole footprints were somehow on the BOM, even though of course they're not a part that I need to place, so I removed them. No biggie. And then I clicked through to the preview, and I was about to just click past and order it. But then I saw that the HUB ICs WERE ROTATED NINETY DEGREES.

![](https://cdn.hackclub.com/019e9087-76ff-7a05-baa7-27c82fe6469b/Screenshot%202026-06-03%20at%207.18.50%E2%80%AFPM.png)

So even though I used an automated plugin, "Fabrication Toolkit" to generate these placement files, I edited it manually to do the hub ICs correctly. It really makes you trust the system less when automated tools fail you like this, but hopefully everything else works. The thing with pcba is that it's kind of out of my hands now, which is both good and bad. Now there's one more funny thing, which is that the IC itself is symmetrical but the pins cannot be used interchangably. So I had to go off of the orientation of the etched "SL2.1S" on the Kicad preview to get things to work. Anyways, it looks good now

![](https://cdn.hackclub.com/019e908d-c87b-70e4-8fbd-449eb6f4aec4/uhub_pcba_journey.png)

Here's an artistic rendition of what I went through.

Anyways, we'll see how this turns out! By the way I also printed out my case, but I might make some tweaks to it.
