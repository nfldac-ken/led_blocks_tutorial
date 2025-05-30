
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


# LED blocks with the BBuBIOLbox : Single to a Block : Modify the code.



## Get the code blocks ready to modify. 
Remove the parts that are no longer needed.


### In the code, find the **on button A pressed **

> Delete **all** the instructions

> - **show leds** 
- **strip set pixel color** 
- **strip set pixel white LED**
- **strip show**
- both the **digital write pin** instructions



### and in the on button B pressed block

> Also delete **all** the instructions, as button A



### and in the on button A+B pressed block

> Delete the **strip show** and 
both the **digital write pin** instructions. 



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
 Find the **on start** block

### in the on start block
Add the following to create some variables to store numbers
we will use later to control the code actions.

> Make a variable by selecting  ``||Variables.make a variable()||``

> and clicking on the **Make a Variable...** black box

> give it the name **targetStart**

Make four more variables  ``||Variables.make a variable()||``

> with the names below

>> - **targetLength** 
- **targetRed** 
- **targetGreen** 
- **targetBlue** 


Add a  ``||Variables.variables set()||`` instruction

> and place it in the **on start** block below the **strip show** instruction

>> use the drop down arrow and select the **targetStart** variable name


**right click** and **Duplicate** (copy) the **set variable** instruction 
and then duplicate three more to end up with one for each of the 
five variables that have now been created.

> use the drop down **v** to select each variable 
once the copy has been dragged into place.



> Now set each of the values by changing the value in the **white circle** 
after the word **to** as below  

>> - **set targetStart to 0** 
- **set targetLength to 10** 
- **set targetRed to 0** 
- **set targetGreen to 0** 
- **set targetBlue to 0** 


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

Move the screen window to find the **on button A pressed ** block.


### In the on button A pressed block

Add a ``||neopixel.strip.clear()||`` instruction.



Add a  ``||Variables.variables set()||`` instruction for
each of the variables below and set the values as below.

> - **targetRed = 50**
- **targetGreen = 50** 
- **targetBlue = 50** 


### Move the screen window to find the on button B block.


Add a ``||neopixel.strip.clear()||`` instruction.



Add a  ``||Variables.variables set()||`` instruction for
each of the variables below and set the values as below. 

> - **targetRed = 0**
- **targetGreen = 0** 
- **targetBlue = 0** 


### Move the screen window to find the on button A+B block.


Add a  ``||Variables.variables set()||`` instruction for
each of the variables below and set the values as below. 

> drop them in below the **strip clear** instruction. 

> - **targetRed = 0**
- **targetGreen = 0** 
- **targetBlue = 0** 
- **targetStart = 0** 
- **targetLength = 10** 



### What do you think that this new code is going to do?

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
input.onButtonPressed(Button.AB, function () {
    strip.clear()
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
    targetStart = 0
    targetLength = 10
    basic.pause(200)
    basic.showLeds(`
        . . . . .
        . . . . #
        . . . # .
        # . # . .
        . # . . #
        `)

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
strip.show()
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

## Create a new Function block 
to control the LED strip

### In a clear space on the screen

Click on **V Advanced** then select  
``||Functions||`` ``||functions.make()||`` ``||a Function||`` block 

> Type in the function name **target**  
in the white box to the right of the word **function** 
replacing the words **do something** 

Then add the function parameters by clicking on the ``||Number||`` button
and typing in the parameter names.

Create the parameters below

> - **targetStart** 
- **targetLength** 
- **targetRed** 
- **targetGreen** 
- **targetBlue** 
                                                         

Click **Done** and then move the new function to a clear space
on the screen.

> if you have placed the function before creating the parameters, 
right click on the function block and select **Edit Function** 
to modify it and add the parameters.

### Add some code instructions
inside the ``||target||`` function add the following..

 > **Neopixel** ``||neopixel.strip.clear()||``

 And below this

 > a **Neopixel** ``||neopixel.set.range()||``

 After the word **to** in the set range instruction, 

>  In the red oval shape, use the drop down **v** arrow to select 
the variable **strip**  if it is not already showing.


 ### In the blue border of the function 

 **Right click duplicate** the parameter **targetStart** and 
 drag and drop the it onto the **white circle** 
 after the words **range from** 
 and also the parameter **targetLength** onto the **white circle**
 after the word **with**.


### Below this add a                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              

  ``||Neopixel||`` ``||neopixel.strip.show.color()||`` 

  > Use the left end drop down arrow **v** to change 
the variable from **strip** to **range**


From the **Neopixel More** menu find a 

 **Neopixel**  **....more**   **red green blue** instruction

> and drag it to dock over the word **red** with an arrow next to it.

 ### In the blue border of the function 

 **Right click duplicate** the parameter **targetRed** and 
 drag and drop the it onto the **white circle** 
 **red**  

>do the same for green and blue replacing them with
the **targetGreen** and **targetBlue** parameters.


When it is called, or activated, this code sends the colour
instruction to a block of LED pixels that are defined by the 
values in the variables that it is sent when it is called. 

In the Function block, these are also called the function's parameters.


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
## Find the forever block
to add some code into it.


### Inside the forever function block

add an **V Advanced**  **Functions**   ``||Functions.call()||`` 
**Your Functions**  **call target** instruction. 

> Dragging and dropping it into the **forever** block.

### Add the function parameter variables.

In the  ``||Variables.variables set()||`` menu

> From the **Your Variables** section, drag a copy of the variable **targetStart** onto the first **white circle** 
after the words **call target**

Do the same for the other white cirlces in the order 

> - **targetLength** 
- **targetRed** 
- **targetGreen** 
- **targetBlue**

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
input.onButtonPressed(Button.AB, function () {
    strip.clear()
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
    targetStart = 0
    targetLength = 10
    basic.pause(200)
    basic.showLeds(`
        . . . . .
        . . . . #
        . . . # .
        # . # . .
        . # . . #
        `)

}) 

basic.forever(function () {
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
})

function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}

```