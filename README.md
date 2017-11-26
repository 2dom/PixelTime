# PixelTime

![PixelTime](/images/PixelTime_small.jpg)

PixelTime is a simple to make weather clock

## Hacking

Most electronics hackers are driven by the quest for the perfect hack. A product of elegance, useful, simple in nature and yet high in impact. A good hack should be high in visual appeal, have good repeatability (and require little skill to do so), be low in costs, manual labour and materials and most importantly should not be too time consuming to make.

By many standards, I believe that PixelTime comes pretty close to my definition of a perfect hack: it is very useful (I also call it the “how to dress the kid’s device”), it is mindboggling simple to make (no soldering or other specialist skills required), looks fantastic, is extremely repeatable (very little manual labour required), costs about 40 EUR and takes about 30 minutes to assemble (+ optional case).

## Display

When I started looking into making a weather clock for my family I naturally started with the central element - the display. Choosing the right display for a project is increasingly difficult since there are so many options! E-Paper, COG LCD, TFT, scanning laser, POV, glow-in-the-dark paper, WS2812B matrix, ferrofluid – you name it. Also, the choice of display defines to some extend the system that drives it. High resolution color varieties require high bus speeds, more memory and processing power. This is less of a problem cost-wise since the availability of the Raspberry Pis Zero, however, then we add the extra complexity of a full blown Linux system we reduce simplicity and repeatability significantly whilst increasing the involved time effort.

In order to keep the complexity on the controller part to a minimum I settled on a ESP8266 based NodeMCU that comes with pre-soldered pin headers. On the display side of things, I chose a Chinese P10 RGB led matrix module that integrates all the necessary driver electronics into a single piece of kit. It offers 32x16=512 RGB pixels with a 1cm spacing for as little as 17 EUR.  The equivalent with WS2812B leds would cost at least twice as much. Furthermore, the P10 module comes fully assembled in a sturdy plastic module frame with defined screw mounts and offers connectivity via two standard pin-headers. Unfortunately, no driver for the ESP8266 existed so I had to write one. [P10_matrix library](https://github.com/2dom/P10_matrix)

## Diffuser and assembly

In order do obtain that vintage computer pixel look, I printed two 16x16 square pixel separator meshes on my 3d printer and glued them together to form one big 32x16 mesh.
To obtain evenly lit pixels I used a sheet of A3 copy paper as a diffuser screen. As the front “glass” I got a piece of 3mm black/transparent acrylic for 10 EUR. For the back, I screwed a another piece of acrylic to the back of the matrix module using the standard screw mounts.

If we put all these things together we end up with something rather elegant: all electrical connections are made using standard Dupont style jumper cables, the module frame, the separator grid and the paper are simply sandwiched between the two pieces of acrylic being screwed together using a few longish M3 screws.

If you have access to a laser cutter for the acrylic, you might get away without any box whatsoever. In my case, I had an old slatted bed-frame lying around that wanted to be used. So after some sawing, gluing and a few layers of Mahogany oil I had a nice box that fits our furniture in style. In order to supply and program PixelTIme, I created another 3D model that allows panel-mounting of the ESP8266. Add a 2A phone charger and a nice 2m USB cable from ebay and voila – PixelTime it is.

## Software

In order for the software to run you will need to open an account with [openweathermap](https://openweathermap.org/) (is free), edit the Wifi network credentials and update the REST request strings with your openweathermap API key and location. Apart from that, you should just be able to flash NodeMCU with the code as is. Flashing the NodeMCU requires  [Arduino](https://www.arduino.cc/en/Main/Software) and the [ESP8266 Arduino core](https://github.com/esp8266/Arduino).

## Bill of materials

1x P10 LED Matrix (Aliexpress) – 17 EUR
20x Dupond jumper cables (Aliexpress) – 0.5 EUR
1x NodeMCU ESP8266 – 3 EUR
2x Acrylics – 10 EUR
1x 3D prints – 3 EUR (plastics)
1x 2A USB charger & 2m cable (ebay) – 8 EUR
10x M3x50mm screws and nuts – 2 EUR
1x Box – Free
