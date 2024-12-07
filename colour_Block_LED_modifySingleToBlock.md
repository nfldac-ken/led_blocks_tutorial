
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
    basic.showLeds(`
        . . . . .
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        `)
    basic.pause(200)
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
})
input.onButtonPressed(Button.B, function () {
    basic.showLeds(`
        # . # . .
        # . # . .
        # . # . .
        # . # . .
        # . # . .
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


# LED blocks with the BBuBIOLbox : A block of LEDs Building the code...



## Starting with your single LED on the box code.


Remove the parts we no longer need for this part.


### In your code, find the ``||input.onButtonPressed(a)||``

delete all the sub-blocks

``||basic:show leds||``

``||neopixel.strip.setPixelColor()||``

``||neopixel.strip.setPixelWhiteLED())||``

``||neopixel.strip.show()||``

both the ``||pins.digitalWritePin()||`` sub-blocks



### and in the ``||input.onButtonPressed(b)||``

delete all the sub-blocks, as button A



### and in the ``||input.onButtonPressed(a+b)||``

both the ``||pins.digitalWritePin()||`` sub-blocks


...


```blocks

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

input.onButtonPressed(Button.A, function () {

})

input.onButtonPressed(Button.B, function () {

})

input.onButtonPressed(Button.AB, function () {
    strip.clear()
    strip.show()
    basic.showLeds(`
        . . . . .
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        `)
    basic.pause(200)

})



```

## And now for some new code
 in the main island blocks
 Find the ``||on start||`` block

### in the on start block
Add the following to create some variables to store numbers
we will use later to control the code actions.

Make a variable by selecting  ``||Variables.make a variable()||``

and clicking on the black Make a Variable... box

give it the name ``||targetStart||``

Make four more variables  ``||Variables.make a variable()||``

with the names below

``||targetLength||``

``||targetRed||``

``||targetGreen||``

``||targetBlue||``


Add a  ``||Variables.variables set()||`` sub-block

and place it in the on start block below the ``||strip show||`` sub-block

use the drop down arrow and select the targetStart variable name

copy the set variable sub-block and create one for each of the variables
that were created above.



Now set each of the values by changing the value after the ``|| to  ||`` as below  

``||set targetStart to 0||``

``||set targetLength to 10||``

``||set targetRed to 0 ||``

``||set targetGreen to 0||``

``||set targetBlue to 0||``


...


``` blocks

let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()

let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetLength = 0
let targetStart = 0

targetStart = 0
targetLength = 10
targetRed = 0
targetGreen = 0
targetBlue = 0

basic.pause(200)
basic.showLeds(`
    . . . . .
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    `)


```


## Add code to execute when the buttons are activated.

Move the screen window to find the on button A block.


### in the on button A pressed block
This code will clear the LED's and set some variables to store numbers
that are used to control the code actions that happen
whend the button is activated.

Add a ``||neopixel.strip.clear()||`` sub-block.



Add a  ``||Variables.variables set()||`` sub-block for
each of the variables below and set the values as below.

``||targetRed = 50||``

``||targetGreen = 50||``

``||targetBlue = 50||``


### Move the screen window to find the on button B block.


Add a ``||neopixel.strip.clear()||`` sub-block.



Add a  ``||Variables.variables set()||`` sub-block for
each of the variables below and set the values as below.

``||targetRed = 0||``

``||targetGreen = 0||``

``||targetBlue = 0||``



What do you think that this new code is going to do?

...

``` blocks

input.onButtonPressed(Button.A, function () {
    strip.clear()
    targetRed = 50
    targetGreen = 50
    targetBlue = 50
})

input.onButtonPressed(Button.B, function () {
    strip.clear()
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
})

```

## Create a new Function block 
to control the LED strip

### In a clear space on the screen

add an ``||V Advanced||``  ``||Functions||``   ``||functions.make()||`` 
``||a Function||`` block

and then on the screen type in the function name ``||target||`` 
in the white box to the right of the word ``||function||``
replacing the words ``||do something||``

Then add the function parameters by clicking on the ``||Number||`` button
and typing in the parameter names.

Create the parameters below

``||targetStart||``
``||targetLength||``
``||targetRed||``
``||targetGreen||``
``||targetBlue||``
                                                         

click ``||Done||`` and then move the new function to a clear space
on the screen.

### Add some code sub-blocks
inside the ``||target||`` function add the following..

 ``||Neopixel||`` ``||neopixel.strip.clear()||``

 and below this

 a ``||Neopixel||`` ``||neopixel.set.range()||``

 After the word ``||to||`` in the set range sub-block,
 use the drop down ``||v||`` arrow to select the variable ``||strip||``
 if it is not already showing.


 ### In the  ``||Variables.variables set()||`` menu

 drag a copy of the variable ``||targetStart||`` onto the white circle
 after the ``||range from||``

 and also of the variable ``||targetLength||`` onto the white circle
 after the ``||with||``


### Below this add a                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              

  ``||Neopixel||`` ``||neopixel.strip.show.color()||``


### From the Neopixel More menu find a

``||Neopixel||``  ``||....more||``   ``||red green blue||`` sub-block

and drag it to dock over the word 'red' with an arrow next to it.

### in the  ``||Variables.variables set()||`` menu

 drag a copy of the variable ``||targetRed||`` onto the white circle
 labelled ``||red||``

do the same for green and blue replacing them with
the ``||targetGreen||`` and ``||targetBlue||`` variables


This code, when it is called, or activated, sends the colour
instruction to a block of LED pixels that are defined by the 
values in the variables that it is send when it is called.
These are also called the function's parameters.


...

``` blocks

let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
targetStart = 0
targetLength = 10
targetRed = 0
targetGreen = 0
targetBlue = 0
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)

function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}

```
## Find and add to the forever block
the code that will continually call the function
to activate the LEDs

### Inside the forever function block

add an ``||V Advanced||``  ``||Functions||``   ``||Functions.call()||`` 
``||Your Functions||``  ``||call target||`` sub-block.
Dragging and dropping it into the forever block.

### Add the function parameter variables.

In the  ``||Variables.variables set()||`` menu

 drag a copy of the variable ``||targetStart||`` onto the first white circle
 after the ``||call target|`` words

 Do the same for the other white cirlces in the order

 ``||targetLength||``
 ``||targetRed||``
 ``||targetGreen||``
 ``||targetBlue||``

This code continually calls, or activates the function
named ``||target||`` passing it the values in the variables.
These are the function parameters.


...

``` blocks

basic.forever(function () {
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
})

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
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
targetStart = 0
targetLength = 10
targetRed = 0
targetGreen = 0
targetBlue = 0
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)

```



--------------

## Check your code.
Is the same as shown by clicking the light bulb hint.

Then click ``|Download|`` to try your code out on the connected MicroBit
to see what it does.

Does it do what you expected?


...

``` blocks

input.onButtonPressed(Button.A, function () {
    strip.clear()
    targetRed = 50
    targetGreen = 50
    targetBlue = 50
})
function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}
input.onButtonPressed(Button.AB, function () {
    strip.clear()
    targetLength = 10
    targetStart = 0
    pins.digitalWritePin(DigitalPin.P13, 1)
    pins.digitalWritePin(DigitalPin.P14, 1)
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
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
    strip.clear()
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
})
let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
targetStart = 0
targetLength = 10
targetRed = 0
targetGreen = 0
targetBlue = 0
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)
basic.forever(function () {
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
})


```
