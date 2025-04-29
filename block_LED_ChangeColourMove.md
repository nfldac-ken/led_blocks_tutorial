
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template


input.onButtonPressed(Button.A, function () {
    strip.clear()
    startStop = 1   
    targetStart += 1
    targetRed = 50
    targetGreen = 50
    targetBlue = 0
})

input.onButtonPressed(Button.B, function () {
    strip.clear()
    startStop = 1  
    targetStart += -1
    targetRed = 0
    targetGreen = 100
    targetBlue = 100
})
input.onButtonPressed(Button.AB, function () {
    startStop = 0
    targetLength = 10
    targetStart = 10
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
    strip.clear()
    strip.show()
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)
    basic.pause(200)
})
function crossHair (crossHairStart: number, crossHairLength: number, crossHairRed: number, crossHairGreen: number, crossHairBlue: number) {
    range = strip.range(crossHairStart, crossHairLength)
    range.showColor(neopixel.rgb(crossHairRed, crossHairGreen, crossHairBlue))
}
function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}
let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetLength = 0
let targetStart = 0
let startStop = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
startStop = 0
targetStart = 10
targetLength = 10
let crossHairStart = 30
let targetDirection = 1
targetRed = 0
targetGreen = 0
targetBlue = 0
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)
basic.forever(function () {
    if (startStop == 1) {
        if (targetStart < 1) {
            targetDirection = 1
        } else {
            if (targetStart > 59) {
                targetDirection = -1
            }
        }
    targetStart += targetDirection
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
    crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
    basic.pause(100)
    }

})





```
# LED blocks with the BBuBIOLbox : A block of LEDs : Colour and Movement : Change the code


## Try the code.
Click ``|Download|`` to try it out on the connected MicroBit and 
to see what it does.


> press one button, then the other, then both together 





## Set some new colours 

In each of the **on button pressed** blocks find the set 
**Red Green Blue** values and change them to your favourite colour. 

> use the Red Green Blue values from the colour wheel handout. 

### Or for a random effect you could use the 

**Math** ``||math.pickrandom()||`` instruction. 

>drag and drop this onto the **set** colour **white circle** 
and change its right hand **white circle** to **255** 

>> do this for **Red Green Blue** to get the full effect. 

### Check your code.
Is it the same as shown by clicking the light bulb hint.

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

### Does it do what you expected? 
When the **red** and **blue** buttons are pressed, 
*separately* and *together*?





``` blocks 
input.onButtonPressed(Button.A, function () {
    strip.clear()
    startStop = 1 
    targetStart += targetDirection * -1
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})


input.onButtonPressed(Button.B, function () {
    strip.clear()
    startStop = 1 
    targetStart += targetDirection
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})




```



## Add some movement and colours to the crossHair pixels. 
.

### Find the **on button A pressed** function block. 
In the **change** instruction use the **v** arrow to select the 
variable **crossHairStart** 

> and check the value is the **white circle** is **1** 


### Find the **on button B pressed** function block. 
In the **change** instruction use the **v** arrow to select the 
variable **crossHairStart** 

> and check the value is the **white circle** is **-1**

This code will activate the movement, and 
move the crossHair start position each time a button is pressed.


### Find the set targetRed instruction

and use the **v** arrow to change it to crossHairRed 
> do the same for the **set green** and **blue** instructions

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

### Does it do what you expected? 





``` blocks

input.onButtonPressed(Button.A, function () {
    strip.clear()
    startStop = 1    
    crossHairStart += 1
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})

input.onButtonPressed(Button.B, function () {
    strip.clear()
    startStop = 1    
    crossHairStart += -1
    crossHairRed = randint(0, 255)
    crossHairGreen = randint(0, 255)
    crossHairBlue = randint(0, 255)
})



```


## Check your code.
Is it the same as shown by clicking the light bulb hint.

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

Does it do what you expected?


...

``` blocks

input.onButtonPressed(Button.A, function () {
    strip.clear()
    startStop = 1    
    crossHairStart += 1
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})

input.onButtonPressed(Button.B, function () {
    strip.clear()
    startStop = 1    
    crossHairStart += -1
    crossHairRed = randint(0, 255)
    crossHairGreen = randint(0, 255)
    crossHairBlue = randint(0, 255)
})
input.onButtonPressed(Button.AB, function () {
    startStop = 0
    targetLength = 10
    targetStart = 10
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
    strip.clear()
    strip.show()
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)
    basic.pause(200)
})
function crossHair (crossHairStart: number, crossHairLength: number, crossHairRed: number, crossHairGreen: number, crossHairBlue: number) {
    range = strip.range(crossHairStart, crossHairLength)
    range.showColor(neopixel.rgb(crossHairRed, crossHairGreen, crossHairBlue))
}
function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}
let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetLength = 0
let targetStart = 0
let startStop = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
startStop = 0
targetStart = 10
targetLength = 10
let crossHairStart = 30
let targetDirection = 1
targetRed = 0
targetGreen = 0
targetBlue = 0
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)
basic.forever(function () {
    if (startStop == 1) {
        if (targetStart < 1) {
            targetDirection = 1
        } else {
            if (targetStart > 59) {
                targetDirection = -1
            }
        }
    targetStart += targetDirection
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
    crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
    basic.pause(100)
    }

})

```