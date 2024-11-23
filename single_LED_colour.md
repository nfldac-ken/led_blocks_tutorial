``package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```
 



# LED blocks with the BBuBIOLbox : Single LED, adding some colour...



## Add some colour to the LED on the box

In your code, find the ``||input.onButtonPressed(a)||`` island block.

In the ``|| strip_0.setPixelColor(0, neopixel.rgb(10, 10, 10)) ||`` sub-block

change the ``||rgb(10,10,10) ||`` values to ``||rgb(100 ,0 ,0) ||`` 

and in the ``|| strip_0.setPixelWhiteLED(0, 10) ||`` sub block

Change it to ``|| strip_0.setPixelWhiteLED(0, 0) ||`` 

### And try it out

Click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

What happens to all the LEDs on the box when you press the ``||red||`` button?



```blocks

input.onButtonPressed(Button.A, function () {
    basic.showLeds(`
        # # . # #
        # # . # .
        # # . # #
        # # . . #
        # # . # #
        `)
    strip_0.setPixelColor(0, neopixel.rgb(100, 0, 0))
    strip_0.setPixelWhiteLED(0, 0)
    strip_0.show()
    pins.digitalWritePin(DigitalPin.P13, 0)
    pins.digitalWritePin(DigitalPin.P14, 1)
})

```

## Lets make our own colour for the LED

Using the RGB Colour wheel, choose you favorite colour and then
put the RGB values into the same sub block.

Put the values in the ``|| strip_0.setPixelColor(0, neopixel.rgb(0, 0, 0)) ||`` sub-block

putting your chosen values in to replace ``|| 0, 0, 0 ||``

and click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

Experinment with some other colours and decide which ones you like best.