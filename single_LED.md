
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```

# LED blocks with the BBuBIOLbox : Single LED



## Add some Neopixel sub-blocks to the on start block
This will set up the LED strip ready for us to use it.

### Set up the LEDs

Add a **set strip** sub-block from the **Neopixel**  ``||neopixel.create()||`` menu

> Change the number of LEDs to read **with 61 leds**.
And use the right hand end drop down arrow **v** to select the LED type as **RGB+W**


Add a  ``||Neopixel||`` ``||....more||`` ``||neopixel.strip.setbrightness()||`` sub-block

> and drop it into the **on start** block below the **set strip** sub-block
change the value in the **white circle** from **255** to **50**

### Clear the LEDs at startup.

Add a Neopixel ``||neopixel.strip.clear()||`` sub-block

> and drop it into the **on start** block below the 
**set strip set brightness** sub-block

Add a Neopixel  ``||neopixel.strip.show()||`` sub-block

> and drop it into the **on start** block below the **strip clear** sub-block


```blocks

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)



strip.clear()
strip.show()


```


## Fill in some more of the start block

This will create the display seen when the MicroBit is restarted
and set up our variables hardware settings so we are ready to go...


### Add a pause for things to settle

drag and drop a  ``||basic:pause||`` into the **onstart** block

> clicking on the drop down arrow **v** to select **200ms**



### Add the display

drag and drop a  ``||basic:show leds||`` into the ``||basic:onstart||`` block

clicking on the squares to turn them white to create a **tick shape**



```blocks

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
    basic.pause(200)
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)


```


## Tidy up and test the code

### Tidy up

Leave the ``||basic:forever()||`` block empty but

click and drag it down below the on start block to
clear the space to the right of your code blocks.

### And try it out

Now click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

You may need to **pair** your Micribit to start the download.


> Is it working correctly?



## Add the code for the first button A

and the code that controls what happens when it is activated


### Add the button function block

Add an ``||input.onButtonPressed(a)||`` from the input menu


### Add the MicroBit display code

drag and drop a  ``||basic:show leds||`` into the on **button A pressed** 
function block

> clicking on the squares to turn them white to create a number **15** shape


### Add the LED NeoPixel code within the button function block

Add a ``||Neopixel||`` ``||....more||``  ``||neopixel.strip.setPixelColor(0, neopixel.red())||`` sub-block

> Find the ``||Neopixel||`` ``||....more||``   ``||red green blue sub-block||``
and drag it to dock over the word **'red'**.

>> Then chage the values from **255 255 255** to **10 10 10**

Add a ``||Neopixel||`` ``||....more||``  ``||neopixel.strip.setPixelWhiteLED())||`` sub-block

> and change the right hand end ** white circle**  value from **0** to **10**




Add a Neopixel  ``||neopixel.strip.show()||`` sub-block

### To drive the box green and yellow LED's

Add an ``||pins.digitalWritePin()||`` from the input menu

> and using the drop down **v** arrow change **P0** to **P13**

Add an ``||pins.digitalWritePin()||`` from the input menu

> using the drop down arrow **v** change **P0** to **P14** and
change the number in the right hand oval from **0** to **1**




### Try it out

Now click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

> What happens to all the LEDs on the box and on the MicroBit display?


>> Is it working correctly?






```blocks

input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        # # . # #
        # # . # .
        # # . # #
        # # . . #
        # # . # #
        `)
    strip.setPixelColor(0, neopixel.rgb(10, 10, 10))
    strip.setPixelWhiteLED(0, 10)
    strip.show()
    pins.digitalWritePin(DigitalPin.P13, 0)
    pins.digitalWritePin(DigitalPin.P14, 1)
})

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
    basic.pause(200)
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)

```

## Add the code for the second button B
and the code that controls what happens when it is activated

### Add a second input button

Add an ``||input.onButtonPressed(a)||`` from the input menu.

> Use the drop down arrow **v** to change it to to **B**.
The block will go from grey to purple showing it is now active.

### Copy each of the sub-blocks from the Button A function

> by right clicking on each one and selecting **Duplicate**. 
A grey copy of the sub-block will appear.

Drag this and dock it into the new Button B function you have just created.

> Make a duplicate of each of the sub-blocks and put them into 
the **on button b pressed** block 

- **show leds**
- **strip set**
- **set pixel white**
- **strip show**
- **digital write pin 13**
- **digital write pin 14**


### Then make the following changes.

Instead of a **15** pattern of white dots, create a number **11** pattern.

In the **strip set** sub-function, change the **red green blue** colour values 
from **10 10 10** to **0 0 0**.

And the **set pixel white LED** right hand **white circle** value to **0**.

Change the **digital write pin P13** value to **1**.

And the **digital write pin P14** to **0**.

### Try it out

Now click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

> What happens to all the LEDs now on the box and on the MicroBit display?

> How is it different from what happens when you press button A?

>> Is it working correctly?




```blocks
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        . # . . #
        # # . # #
        . # . . #
        . # . . #
        . # . . #
        `)
    strip.setPixelColor(0, neopixel.rgb(0, 0, 0))
    strip.setPixelWhiteLED(0, 0)
    strip.show()
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 0)
})

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
    basic.pause(200)
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)

```


## Add the code for the buttons A and B pressed together
and the code that controls what happens when it is activated


### and the code that controls what happens when it is activated

### Add a Third input button

Add an ``||input.onButtonPressed(a)||`` from the input menu. 

> Change the drop down arrow **v** to **A+B**.

> The block will go from grey to purple showing it is now active.

### Copy the following sub-blocks from the on start function

Drag the grey copies and dock them into the new **Button A+B** function 
you have just created.

> Do this for each of the sub-blocks.

- **neopixel.strip.clear()** sub-block

- **neopixel.strip.show()** sub-block

- **basic:pause**

- **basic:show leds**




 And from the Button A function

> - **digital write pin P13** 
- **digital write pin P14**



### Then make the following changes.

Change the **pause ms** to **200**

Make the pattern of **white dots**, create a **tick shape with an extra dot in the corner**.

Check and change if required, the **digital write pin P13** value to **1**.

Check and change if required, the **digital write pin P14** value to **1**.

### Try it out

Click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

> What happens to all the LEDs now on the box and on the MicroBit display?

> How is pressing both buttons together different 
from what happens when you press button A or B?

> Is it working correctly?


```blocks

input.onButtonPressed(Button.AB, function () {
    strip.clear()
    strip.show()
    basic.pause(200)    
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
})

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
    basic.pause(200)
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)

```