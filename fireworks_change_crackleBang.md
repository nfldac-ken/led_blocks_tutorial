
```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template

function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start < 1) {
            pattern02Direction = 1
        } else {
            if (pattern02Start > 59) {
                pattern02Direction = -1
            }
        }
        pattern02Start += pattern02Direction
        rangeRed = 5 * 1
        rangeGreen = 5 * 20
        rangeBlue = 5 * 20
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), pattern02Length)
        range.showColor(neopixel.rgb(rangeRed, rangeGreen, rangeBlue))
        range02Red = 5 * 20
        range02Green = 5 * 1
        range02Blue = 5 * 1
        range02 = strip_0.range(randint(randint(0, 51), pattern02Start + pattern02Length + pattern02Start * 2), pattern02Length)
        range02.showColor(neopixel.rgb(range02Red, range02Green, range02Blue))
    }
}
input.onButtonPressed(Button.A, function () {
    pattern01StartStop = 1
    pattern01Length = 3
    pattern01Start = 0
    pattern02Start = 0
    for (let index = 0; index <= 50; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(50)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 3
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(50)
        }
        Pattern02StartStop = 0
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
            pattern01Start = randint(0, pattern01Length)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(60 - pattern01Length, 60)
            }
        }
        pattern01Red = 5 * 10
        pattern01Green = 5 * 2
        pattern01Blue = 5 * 1
        range = strip_0.range(pattern01Start, 5)
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}
input.onButtonPressed(Button.B, function () {
    pattern01StartStop = 1
    pattern01Length = 3
    pattern01Start = 60
    pattern02Start = 60
    for (let index = 0; index <= 50; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(50)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 3
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(50)
        }
        Pattern02StartStop = 0
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
let pattern01Start = 0
let pattern01Length = 0
let pattern01StartStop = 0
let range02: neopixel.Strip = null
let range02Blue = 0
let range02Green = 0
let range02Red = 0
let pattern02Length = 0
let range: neopixel.Strip = null
let rangeBlue = 0
let rangeGreen = 0
let rangeRed = 0
let pattern02Direction = 0
let pattern02Start = 0
let Pattern02StartStop = 0
let strip_0: neopixel.Strip = null
strip_0 = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip_0.setBrightness(100)
strip_0.clear()
strip_0.show()
pins.digitalWritePin(DigitalPin.P13, 1)
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


# LED Fireworks with the BBuBIOLbox : Pattern Crackle Bang : Change the code


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

> find the **set pattern01Length** instruction

>> and change the value in the **white circle** to **10**




> find the  **pattern02Length** instruction 

>> and change the value in the **white circle** to **10**


Then click ``|Download|`` to to see what the changes have done. 


### Still in the on button A pressed fuction 
Find the green **for index** loop instruction 

> change the **from 0** to **white circle** from **50** to a bigger number, 
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
    pattern01StartStop = 1
    pattern01Length = 10
    pattern01Start = 0
    pattern02Start = 0
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(5)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 10
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(3)
        }
        Pattern02StartStop = 0
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})

input.onButtonPressed(Button.B, function () {
    pattern01StartStop = 1
    pattern01Length = 10
    pattern01Start = 50
    pattern02Start = 60
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(5)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 10
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(3)
        }
        Pattern02StartStop = 0
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
 
and the **set rangeRed, rangeGreen, and rangeBlue** instructions within it 

> these are towards the bottom of the dark blue function block  

Change the values in the right hand **white circle** to create some 
new colours.


> to see each change 
Click ``|Download|`` to try it out.

### Do the same in 

**Function Pattern02** 

> changing both  **set rangeRed, rangeGreen, and rangeBlue** 
and **set range02Red, range02Green, and range02Blue**

and see how the colours work there too 


## Try some random colours 
again in the **function Pattern01** 
dark blue block 

>find the **rangeRed, rangeGreen, and rangeBlue** 
colour instructions 

>> Drag and drop a **Math** ``||math.pickrandom()||`` instruction 
onto the right most **white circle** 
and change its right hand **white circle** to **51**


### Do the same in 

**Function Pattern02** 

> changing both  **set rangeRed, rangeGreen, and rangeBlue** 
and **set range02Red, range02Green, and range02Blue** 

and see how the colours work there too 

This will make the pixels change to different colours each time  
the pattern changes. 


Then click ``|Download|`` to to see what it does. 



>> try some different ramdom **to** values, less than **51**, 
on some of the colour instructions, and see what 
happens 

``` blocks


function Pattern01 (pattern01Length: number) {
    if (pattern01StartStop == 1) {
        strip_0.clear()
        if (pattern01Start < 30) {
            pattern01Start = randint(0, pattern01Length)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(60 - pattern01Length, 60)
            }
        }
        pattern01Red = 5 * randint(0, 51)
        pattern01Green = 5 * randint(0, 5)
        pattern01Blue = 5 * randint(0, 51)
        range = strip_0.range(pattern01Start, randint(0, 5))
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}

function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start < 1) {
            pattern02Direction = 1
        } else {
            if (pattern02Start > 59) {
                pattern02Direction = -1
            }
        }
        pattern02Start += pattern02Direction
        rangeRed = 5 * randint(0, 51)
        rangeGreen = 5 * randint(0, 51)
        rangeBlue = 5 * randint(0, 51)
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), pattern02Length)
        range.showColor(neopixel.rgb(rangeRed, rangeGreen, rangeBlue))
        range02Red = 5 * randint(0, 51)
        range02Green = 5 * randint(0, 51)
        range02Blue = 5 * randint(0, 51)
        range02 = strip_0.range(randint(pattern02Start + pattern02Length, pattern02Start + pattern02Length + pattern02Start * 2), pattern02Length)
        range02.showColor(neopixel.rgb(range02Red, range02Green, range02Blue))
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


``` blocks


let pattern01Blue = 0
let pattern01Green = 0
let pattern01Red = 0
let pattern01Start = 0
let pattern01Length = 0
let pattern01StartStop = 0
let range02: neopixel.Strip = null
let range02Blue = 0
let range02Green = 0
let range02Red = 0
let pattern02Length = 0
let range: neopixel.Strip = null
let rangeBlue = 0
let rangeGreen = 0
let rangeRed = 0
let pattern02Direction = 0
let pattern02Start = 0
let Pattern02StartStop = 0
let strip_0: neopixel.Strip = null
strip_0 = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip_0.setBrightness(100)
strip_0.clear()
strip_0.show()
pins.digitalWritePin(DigitalPin.P13, 1)
pins.digitalWritePin(DigitalPin.P14, 1)
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)



input.onButtonPressed(Button.A, function () {
    pattern01StartStop = 1
    pattern01Length = 10
    pattern01Start = 0
    pattern02Start = 0
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(5)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 10
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(3)
        }
        Pattern02StartStop = 0
    }
    pins.digitalWritePin(DigitalPin.P14, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P14, 1)
    strip_0.clear()
    strip_0.show()
})

input.onButtonPressed(Button.B, function () {
    pattern01StartStop = 1
    pattern01Length = 10
    pattern01Start = 50
    pattern02Start = 60
    for (let index = 0; index <= 300; index++) {
        Pattern01(pattern01Length)
        index += 1
        basic.pause(5)
    }
    pins.digitalWritePin(DigitalPin.P13, 0)
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P13, 1)
    Pattern02StartStop = 1
    pattern02Length = 10
    while (Pattern02StartStop == 1) {
        for (let index = 0; index < 1 * 60; index++) {
            Pattern02(pattern02Length)
            basic.pause(3)
        }
        Pattern02StartStop = 0
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
            pattern01Start = randint(0, pattern01Length)
        } else {
            if (pattern01Start > 30) {
                pattern01Start = randint(60 - pattern01Length, 60)
            }
        }
        pattern01Red = 5 * randint(0, 51)
        pattern01Green = 5 * randint(0, 5)
        pattern01Blue = 5 * randint(0, 51)
        range = strip_0.range(pattern01Start, randint(0, 5))
        range.showColor(neopixel.rgb(pattern01Red, pattern01Green, pattern01Blue))
    }
}

function Pattern02 (pattern02Length: number) {
    if (Pattern02StartStop == 1) {
        strip_0.clear()
        if (pattern02Start < 1) {
            pattern02Direction = 1
        } else {
            if (pattern02Start > 59) {
                pattern02Direction = -1
            }
        }
        pattern02Start += pattern02Direction
        rangeRed = 5 * randint(0, 51)
        rangeGreen = 5 * randint(0, 51)
        rangeBlue = 5 * randint(0, 51)
        range = strip_0.range(randint(pattern02Start, pattern02Start + pattern02Length), pattern02Length)
        range.showColor(neopixel.rgb(rangeRed, rangeGreen, rangeBlue))
        range02Red = 5 * randint(0, 51)
        range02Green = 5 * randint(0, 51)
        range02Blue = 5 * randint(0, 51)
        range02 = strip_0.range(randint(pattern02Start + pattern02Length, pattern02Start + pattern02Length + pattern02Start * 2), pattern02Length)
        range02.showColor(neopixel.rgb(range02Red, range02Green, range02Blue))
    }
}


basic.forever(function () {
	
})

```