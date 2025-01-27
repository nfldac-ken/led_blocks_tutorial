
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template
    
input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        # . # # #
        # . # . .
        # . # # #
        # . . . #
        # . # # #
        `)
    strip.setPixelColor(0, neopixel.rgb(10, 10, 10))
    strip.setPixelWhiteLED(0, 10)
    strip.show()
    pins.digitalWritePin(DigitalPin.P13, 0)
    pins.digitalWritePin(DigitalPin.P14, 1)
})
input.onButtonPressed(Button.AB, function () {
    strip.clear()
    strip.show()
    basic.pause(200)
    basic.showLeds(`
        . . . . .
        . . . . #
        . . . # .
        # . # . .
        . # . . #
        `)
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        # . . . #
        # . . . #
        # . . . #
        # . . . #
        # . . . #
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
    . . . . .
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    `)
basic.forever(function () {
	
})
```


# LED blocks with the BBuBIOLbox : Single LED : Adding colour : Change the code.

## Try the code.
Click ``|Download|`` to try it out on the connected MicroBit and 
to see what it does.


> press one button, then the other, then both together  


## Add some colour to the LED on the box

In the code blocks, find the **on button A pressed** island block.

> In the ** strip set pixel color** instruction

>> change the **rgb(10,10,10)** values to **rgb(100 ,0 ,0)** 

And in the **set pixel white LED** sub block

> Change the numbers in the two **white circles** to read ** 0 to 0**

### And try it out

Click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

What happens to all the LEDs on the box when you press the **red** button?



```blocks

input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        # # . # #
        # # . # .
        # # . # #
        # # . . #
        # # . # #
        `)
    strip.setPixelColor(0, neopixel.rgb(100, 0, 0))
    strip.setPixelWhiteLED(0, 0)
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
    . . . . .
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    `)
    
```

## Lets make our own colour for the LED

Using the RGB Colour wheel, choose you favorite colour.

Staying with the **on button A pressed** block.
Choose your favorite colour from the colour wheel and note the
**R G B** (red, green, blue) number values.

> Put the values in the **set pixel color** instruction

putting your chosen values in to replace **100, 0, 0**

and click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

Experiment with some other colours and decide which ones you like best.

And try changing the colour values from 255 to lower numbers
to generate some more subtle colours.


...
