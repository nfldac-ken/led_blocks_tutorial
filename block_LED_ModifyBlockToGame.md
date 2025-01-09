
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template
input.onButtonPressed(Button.A, function () {
    startStop = 1
    strip.clear()
    crossHairStart += 1
    targetRed = 50
    targetGreen = 50
    targetBlue = 0
})

input.onButtonPressed(Button.B, function () {
    startStop = 1
    strip.clear()
    crossHairStart += -1
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
    }
    targetStart += targetDirection
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
    crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
    basic.pause(100)
})


```


# LED blocks with the BBuBIOLbox : A block of LEDs : Catch Game : Modify the code


## Starting from the moving blocks of LEDs. 
Add some new instructions 

Find the forever block and Add a  ``||Variables.variables set()||`` instruction

> and place it in the **forever** block below the **set targetDirection = 1** instruction

>> use the drop down arrow and select the **targetRed** variable name
>> set the value in the **white circle** to **50** 

>> do the same adding more **set** instructions to make 
>>- **targetGreen = 50**
- **targetBlue = 50**

> **right click** and duplicate each of the **set targetRed, Green, Blue** 
instructions and move them into the lower **if** instruction 
below the **set targetDirection = -1** instruction 


This code sets the colour of the moving block each time it reaches 
end of the strip.

> If you want it to change to a random colour each time it reaches the end 
replace the number in the **white circles** with a 
**Math** ``||math.pickrandom()||`` instruction. 

### Check your code.
Is it the same as shown by clicking the light bulb hint.

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

### Does it do what you expected? 


``` blocks


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

function crossHair (startPosition: number, endPosition: number, crossHairRed: number, CrossHairGreen: number, CrossHairBlue: number) {
    range = strip.range(startPosition, endPosition)
    range.showColor(neopixel.rgb(crossHairRed, CrossHairGreen, CrossHairBlue))
}
function target (targetStartPosition: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStartPosition, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}

let targetDirection = 0
let score = 0
let range: neopixel.Strip = null
let startStop = 0
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let crossHairStart = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(51)
strip.clear()
strip.show()
targetStart = 0
targetLength = 10
crossHairStart = 30
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
targetRed = 50
targetGreen = 50
targetBlue = 50
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)




```

## And to control the game. Button A (red).
Find the **on button A pressed** block 

Add a ``||logic.if()||`` instruction
and dropp it just below the **change crossHairStart** instruction 

> select another  ``||logic.if()||`` instruction
and drop it underneath the first **if** instruction 

### Drag and drop the set target Red, Green, Blue sub blocks
inside the first **if** instruction 

>> check the values are **Red 255, Green 0, Blue 0**. 

>>This is the colour when the target is hit. 
Choose a different colour if you like.


>> Add a  ``||Variables.variables change()||`` instruction 

>> and drop it inside at the top of the top **if** instruction 

In the **change** instruction use the **v** arrow to select the 
variable **targetLength** 

> and check the value is the **white circle** is **-1**. 

>> This reduces the target length by one pixel each time 
it is hit. 



> Make a duplicate of each of the **set targetRed, Green, Blue** 
instructions placing them inside the lower **if** instruction 

>> change the values to **Red 0, Green 0, Blue 255**. 

>>This is the colour when the game is won. 
If you choose your own colour, make sure it is different from 
the target hit colour. 


>> Add a  ``||Variables.variables set()||`` instruction 

>> and drop it inside at the top of the lower **if** instruction 

In the **set** instruction use the **v** arrow to select the 
variable **targetLength** 

> and check the value is the **white circle** is **61**. 

>> This makes the game win pixels cover the full length of the strip. 



### Set up the logic actions 
> select a ``||logic.compare and v||`` **0 =v 0** instruction 

>> this is the a vee shaped ended instruction 
towards the bottom of the list. 


>> drop this into the darker same shape in the top **if** instruction 

>> and do the same for the lower **if** instruction 

> select a ``||logic.compare(=)||`` ** = ** instruction 
>> this is the first of the vee shaped ended instructions 
towards the bottom of the list. 

>> drop this into the box the darker same shapes at either side 
of the **and v** comparison instructions. 

> do the same for the lower **if** comparison.



### Set up the compare instructions 
From the ``||Variables.your variables()||`` menu pick 
the **crossHairStart** red oval and drop it onto the left hand 
**white circle** at the top of the first **if compare =** instruction 

> and drop **targetStart** into the second **white circle**. 

>> use the drop down arrows **v** to change the compare instruction 
to look like 
- **crossHairStart > targetStart** 

>> From the ``||Math.Math()||`` menu 
pick a **0 +v 0** instruction and drop it onto 
the far right hand **white circle**, in the top **if** compare instruction. 

From the ``||Variables.your variables()||`` menu pick 
the **crossHairStart** red oval and drop it onto the top 
**if compare**, into the first remaining **white circle** 

>and then drop **targetStart** into the next **white circle** and 
drop **targetLength** into the last **white circle**

### For the lower if compare

Do the same for the other compare **white circles** from 
left to right, top to bottom to read as below 

>> - ** crossHairStart > targetStart and v targetStart + targetLength** 

for the upper **if** and 

>> - **crossHairStart =targetStart and v targetLength = 1** 

for the lower **if** 


Click on the **lightbulb** hint to check your code.

>> This is the most complex part of the code. 

>>It checks where the moving target LED pixels are 
compared to where the crossHair pixels are, 
and changes the colour, and length, of the moving pixels depending on 
the outcome. 

>> It also checks if the game is won, when the last pixel is hit. 
Changing the colour and length of the pixels when it happens. 

..

``` blocks


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
    if (crossHairStart == targetStart && targetLength == 1) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
})


let targetDirection = 0
let score = 0
let range: neopixel.Strip = null
let startStop = 0
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let crossHairStart = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(51)
strip.clear()
strip.show()
targetStart = 0
targetLength = 10
crossHairStart = 30
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
targetRed = 50
targetGreen = 50
targetBlue = 50
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)




```

## And to control the game. Button B (blue)
Find the **on button B pressed** block 


### Delete it.

> Then **right click** and **duplicate** the **on button A pressed** function. 

>> dropping it into a clear space.

Using the drop down arrow **v** Change the **A** to **B**. 

> the block will change from grey to pink. 

### Just below the strip clear instruction 
Change the value of the **change crossHairStart** from **-1** to **1**

> This makes the crossHair move in the opposite direction to 
how it moves when the other button is pressed.


Click on the **lightbulb** hint to check your code.



``` blocks


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
    if (crossHairStart == targetStart && targetLength == 1) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
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
    if (crossHairStart == targetStart && targetLength == 1) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
})

let targetDirection = 0
let score = 0
let range: neopixel.Strip = null
let startStop = 0
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let crossHairStart = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(51)
strip.clear()
strip.show()
targetStart = 0
targetLength = 10
crossHairStart = 30
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
targetRed = 50
targetGreen = 50
targetBlue = 50
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)


```






## Check your code.
Is it the same as shown by clicking the light bulb hint.

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

Try to catch the moving target by moving the crossHair as the target pixels  
pass through it. 

Does it do what you expected? 


...

``` blocks


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
    if (crossHairStart == targetStart && targetLength == 1) {
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
    targetLength = 10
    crossHairStart = 30
    score = 30
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
    if (crossHairStart == targetStart && targetLength == 1) {
        targetLength = 61
        targetRed = 0
        targetGreen = 0
        targetBlue = 255
    }
})
let targetDirection = 0
let score = 0
let range: neopixel.Strip = null
let startStop = 0
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let crossHairStart = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(51)
strip.clear()
strip.show()
targetStart = 0
targetLength = 10
crossHairStart = 30
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
targetRed = 50
targetGreen = 50
targetBlue = 50
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

### To change the speed of the game 

find the **pause** instruction. 

> and change it to a lower number to make the game 
go faster!

Then click ``|Download|`` to to see what it does. 


``` blocks

let targetDirection = 0
let score = 0
let range: neopixel.Strip = null
let startStop = 0
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let crossHairStart = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(51)
strip.clear()
strip.show()
targetStart = 0
targetLength = 10
crossHairStart = 30
let crossHairRed = 100
let crossHairGreen = 1
let crossHairBlue = 100
targetRed = 50
targetGreen = 50
targetBlue = 50
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
        }
        targetStart += targetDirection
        target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
        crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
        basic.pause(100)
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
## Hit and win colours. 

In the **on button A pressed** and **on button B** pressed 
functions.

> In the top **if** instruction change the colours 
to your favourite for when the target is hit. 

> and in the lower **if**, change the win colour as you like. 
Maybe use another set of **pick random** instructions instead of 
fixed values. 

Then click ``|Download|`` to to see what your choices look like.

Can you complete the game any quicker now?

Time yourself and compare it with the other groups.



..