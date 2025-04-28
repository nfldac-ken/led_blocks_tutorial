

```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template

input.onButtonPressed(Button.A, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 0
    pattern02Start = 0
    pattern02Length = 5
    pattern01Length = 2
    for (let index = 0; index <= 50; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(100)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start < 59) {
        Pattern02(pattern02Length)
        basic.pause(100)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})
function Pattern01 (pattern01Length: number) {
    if (pattern01StartStop == 1) {
        strip_0.clear()
        if (pattern01Start < 30) {
            pattern01Start = randint(0, 10)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(50, 60)
            }
        }
        pattern01Red = 5 * 25
        pattern01Green = 5 * 5
        pattern01Blue = 5 * 0
        range = strip_0.range(pattern01Start, pattern01Length)
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}
function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start > 59) {
            pattern02Direction = -1
        } else {
            if (pattern02Start < 1) {
                pattern02Direction = 1
            }
        }
        pattern02Start += pattern02Direction
        pattern02Red = 5 * 0
        pattern02Green = 5 * 20
        pattern02Blue = 5 * 20
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), 4)
        range.showColor(neopixel.rgb(pattern02Red, pattern02Green, pattern02Blue))
    }
}
input.onButtonPressed(Button.B, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 60
    pattern02Start = 60
    pattern02Length = 5
    pattern01Length = 2
    for (let index = 0; index <= 50; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(100)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start > 1) {
        Pattern02(pattern02Length)
        basic.pause(100)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})
let pattern01Blue = 0
let pattern01Green = 0
let pattern01Red = 0
let pattern01Length = 0
let pattern01Start = 0
let pattern01StartStop = 0
let pattern02Length = 0
let range: neopixel.Strip = null
let pattern02Blue = 0
let pattern02Green = 0
let pattern02Red = 0
let pattern02Direction = 0
let pattern02Start = 0
let Pattern02StartStop = 0
let strip_0: neopixel.Strip = null
strip_0 = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip_0.setBrightness(100)
strip_0.clear()
strip_0.show()
pins.digitalWritePin(DigitalPin.P14, 1)
pins.digitalWritePin(DigitalPin.P14, 1)
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)
basic.forever(function () {
	
})





```


# LED Fireworks with the BBuBIOLbox : Pattern Crackle Whoosh : Change the code


## Try the code.
Click ``|Download|`` to try it out on the connected MicroBit and 
to see what it does.


> press one button, and watch the pattern 

>> then the other to see the difference 

These are two versions of the firework patterns 

> Starting at different ends of the LED strip 

>> which can later be joined together with the rest of the team's 
LED strips to make a full display 




## To make the pattern more interesting 
and start to customise the display  



### Change the code in the buttons 
to make the patterns behave differently.

#### Find the function 
**on button A v pressed**

> find the **set patter01Length** instruction

>> and change the value in the **white circle** to **1**




> find the  **pattern02Length** instruction 

>> and change the value in the **white circle** to **10**


Then click ``|Download|`` to to see what the changes have done. 


### Still in the on button A pressed fuction 
Find the green **for index** loop instruction 

> change the **from 0** to **white cirlce** from **50** to a bigger number, 
this makes the pattern last longer 

> and make the **pause (ms)** value lower by typing in a lower number, 
this makes it run faster  

### Find the green 
**while pattern02Start** instruction and change the 
**pause (ms)** white circle value to a lower value to 
speed up pattern 2

Then click ``|Download|`` to to see what the changes have done. 


### Try a few different combinations 
clicking ``|Download|`` to to see what they do. 

> and when it looks good on the A button, change the same value 
in the **on button B v pressed** 
function and check that it looks the same as the pattern 
moves up or down the strip after you press the **A** or **B** button.

> you can click on the light bulb at the bottom left of the instruction pane 
to see how it might look.




...



```blocks

input.onButtonPressed(Button.A, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 0
    pattern02Start = 0
    pattern02Length = 10
    pattern01Length = 1
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(20)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start < 59) {
        Pattern02(pattern02Length)
        basic.pause(10)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})
input.onButtonPressed(Button.B, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 60
    pattern02Start = 60
    pattern02Length = 10
    pattern01Length = 1
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(20)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start > 1) {
        Pattern02(pattern02Length)
        basic.pause(10)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})


```

## To make things a bit more colourful 
and start to customise the display  

### Find the function 

 **Function Pattern01 ** 
 
and the **set pattern01Red, Green, and Blue** instructions within it 

> these are towards the bottom of the dark blue function block  

Change the values in the right hand **white circle** to create some 
new colours.

> to see each change 
Click ``|Download|`` to try it out.

### Do the same in 

**Function Pattern02** 

and see how the colours work there too 


## Try some random colours 
again in the **function Pattern01**
dark blue block

>find the **set Pattern01Red, Pattern01Green, Pattern01Blue** 
colour instructions 


>> Drag and drop a **Math** ``||math.pickrandom()||`` instruction 
onto the right most **white circle** 
and change its right hand **white circle** to **51**



This will make the pixels change to different colours each time  
the pattern changes. 


Then click ``|Download|`` to to see what it does. 

### do the same for **function Pattern02** function block 
find the **set Pattern02Red, Pattern02Green, Pattern02Blue** instructions


>> try some different ramdom **to** values, less than **51**, 
on some of the colour instructions, and see what 
happens 



``` blocks




function Pattern01 (pattern01Length: number) {
    if (pattern01StartStop == 1) {
        strip_0.clear()
        if (pattern01Start < 30) {
            pattern01Start = randint(0, 10)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(50, 60)
            }
        }
        pattern01Red = 5 * randint(0, 51)
        pattern01Green = 5 * randint(0, 51)
        pattern01Blue = 5 * randint(0, 10)
        range = strip_0.range(pattern01Start, pattern01Length)
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}
function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start > 59) {
            pattern02Direction = -1
        } else {
            if (pattern02Start < 1) {
                pattern02Direction = 1
            }
        }
        pattern02Start += pattern02Direction
        pattern02Red = 5 * randint(0, 51)
        pattern02Green = 5 * randint(0, 10)
        pattern02Blue = 5 * randint(0, 51)
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), 2)
        range.showColor(neopixel.rgb(pattern02Red, pattern02Green, pattern02Blue))
    }
}



```

## Troubleshooting  

If you have a problem and need to check all your code, 
click on the lightbulb tip to see a full example 

### Once you are happy with the results
>> These patterns are now ready to be used with the rest of the team 
to create a full display using several strips of pixels 
..

```blocks

let pattern01Blue = 0
let pattern01Green = 0
let pattern01Red = 0
let pattern01Length = 0
let pattern01Start = 0
let pattern01StartStop = 0
let pattern02Length = 0
let range: neopixel.Strip = null
let pattern02Blue = 0
let pattern02Green = 0
let pattern02Red = 0
let pattern02Direction = 0
let pattern02Start = 0
let Pattern02StartStop = 0
let strip_0: neopixel.Strip = null
strip_0 = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip_0.setBrightness(100)
strip_0.clear()
strip_0.show()
pins.digitalWritePin(DigitalPin.P14, 1)
pins.digitalWritePin(DigitalPin.P14, 1)
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)
basic.forever(function () {
	
})

input.onButtonPressed(Button.A, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 0
    pattern02Start = 0
    pattern02Length = 10
    pattern01Length = 1
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(20)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start < 59) {
        Pattern02(pattern02Length)
        basic.pause(10)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})

input.onButtonPressed(Button.B, function () {
    Pattern02StartStop = 1
    pattern01StartStop = 1
    pattern01Start = 60
    pattern02Start = 60
    pattern02Length = 10
    pattern01Length = 1
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(20)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    while (pattern02Start > 1) {
        Pattern02(pattern02Length)
        basic.pause(10)
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})
function Pattern01 (pattern01Length: number) {
    if (pattern01StartStop == 1) {
        strip_0.clear()
        if (pattern01Start < 30) {
            pattern01Start = randint(0, 10)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(50, 60)
            }
        }
        pattern01Red = 5 * randint(0, 51)
        pattern01Green = 5 * randint(0, 51)
        pattern01Blue = 5 * randint(0, 10)
        range = strip_0.range(pattern01Start, pattern01Length)
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}
function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start > 59) {
            pattern02Direction = -1
        } else {
            if (pattern02Start < 1) {
                pattern02Direction = 1
            }
        }
        pattern02Start += pattern02Direction
        pattern02Red = 5 * randint(0, 51)
        pattern02Green = 5 * randint(0, 10)
        pattern02Blue = 5 * randint(0, 51)
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), 2)
        range.showColor(neopixel.rgb(pattern02Red, pattern02Green, pattern02Blue))
    }
}

```
