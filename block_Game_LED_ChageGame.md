
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template

input.onButtonPressed(Button.A, function () {
    startStop = 1
    strip.clear()
    crossHairStart += 1
    // Score a hit make target smaller and red
    if (crossHairStart > targetStart && crossHairStart < targetStart + targetLength) {
        targetLength += -1
        targetRed = 255
        targetGreen = 0
        targetBlue = 0
    }
    if (crossHairStart == targetStart && targetLength < 2) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
})
function crossHair (startPosition: number, endPosition: number, crossHairRed: number, CrossHairGreen: number, CrossHairBlue: number) {
    range = strip.range(startPosition, endPosition)
    range.showColor(neopixel.rgb(crossHairRed, CrossHairGreen, CrossHairBlue))
}
function target (targetStartPosition: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStartPosition, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}
input.onButtonPressed(Button.AB, function () {
    startStop = 0
    targetLength = 10
    targetStart = 0
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
input.onButtonPressed(Button.B, function () {
    startStop = 1
    strip.clear()
    crossHairStart += -1
    if (crossHairStart > targetStart && crossHairStart < targetStart + targetLength) {
        targetLength += -1
        targetRed = 255
        targetGreen = 0
        targetBlue = 0
    }
    if (crossHairStart == targetStart && targetLength < 2) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
})
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
targetStart = 0
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
            targetRed = 50
            targetGreen = 50
            targetBlue = 50
        } else {
            if (targetStart > 59) {
                targetDirection = -1
                targetRed = 50
                targetGreen = 50
                targetBlue = 50
            }        
        }
        targetStart += targetDirection
        target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
        crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
        basic.pause(100)  
    }
})




```


# LED blocks with the BBuBIOLbox : A block of LEDs : Catch Game : Change the code


## Try the code.
Click ``|Download|`` to try it out on the connected MicroBit and 
to see what it does.


> press one button, then the other, and try to 
do the press when the moving block is underneath the block of 
two pixels 

> Then try pressing both buttons together 



## To make things a bit more colourful 
and the game a bit harder to do. 

### Find the forever function. 
and the **set** instructions inside both the **if** instructions. 

> Drag and drop a **Math** ``||math.pickrandom()||`` instruction. 

>> drag and drop this onto the **set** colour **white circle** 
and change its right hand **white circle** to **255** 

>> do this for **Red Green Blue** to get the full effect. 

This will make the target change colour each time it 
reaches the end of the LED strip. 


Then click ``|Download|`` to to see what it does. 





``` blocks

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
            targetRed = randint(0, 255)
            targetGreen = randint(0, 255)
            targetBlue = randint(0, 255)
        } else {
            if (targetStart > 59) {
                targetDirection = -1
                targetRed = randint(0, 255)
                targetGreen = randint(0, 255)
                targetBlue = randint(0, 255)
            }
        targetStart += targetDirection
        target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
        crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
        basic.pause(100)
        }

    }
})

function crossHair (startPosition: number, endPosition: number, crossHairRed: number, CrossHairGreen: number, CrossHairBlue: number) {
    range = strip.range(startPosition, endPosition)
    range.showColor(neopixel.rgb(crossHairRed, CrossHairGreen, CrossHairBlue))
}
function target (targetStartPosition: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStartPosition, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}

})

```

## To change the speed of the game 

In the **forever** function 

find the **pause** instruction. 

> and change it to a lower number to make the game 
go faster!

Then click ``|Download|`` to to see what it does. 

```blocks

basic.forever(function () {
    if (startStop == 1) {
        if (targetStart < 1) {
            targetDirection = 1
            targetRed = randint(0, 255)
            targetGreen = randint(0, 255)
            targetBlue = randint(0, 255)
        } else {
            if (targetStart > 59) {
                targetDirection = -1
                targetRed = randint(0, 255)
                targetGreen = randint(0, 255)
                targetBlue = randint(0, 255)
            }
        targetStart += targetDirection
        target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
        crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
        basic.pause(1)
        }

    }
})

```
## Hit and win colours. 

In the **on button A pressed** and **on button B** pressed 
functions.

> In the top **if** instruction change the colours 
to your favourite for when the target is hit. 

> and in the lower **if**, change the win colour as you like. 
Maybe use another set of **pick random** instructions instead of 
fixed values. 

Then click ``|Download|`` to to see what your choices look like.


### See how fast you complete the game 

> Time yourself and compare the result with the other groups.



..
