```package

neopixel=github:microsoft/pxt-neopixel#v0.7.5

```


```template

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


# LED blocks with the BBuBIOLbox : A block of LEDs : Colour and Movement : Modify the code


## Add some new code 
Add the following to create some variables to store numbers
we will use later to control the code actions.

### Make some new variables 

> Make a variable by selecting  ``||Variables.make a variable()||``

> and clicking on the **Make a Variable...** black box

> give it the name **crossHairStart**

Make four more variables  ``||Variables.make a variable()||``

> with the names below

>> - **targetDirection**  
- **crossHairRed** 
- **crossHairGreen** 
- **crossHairBlue** 


### Set up the variables 
In the code find the **on start** block.

Add a  ``||Variables.variables set()||`` instruction

> and place it in the **on start** block below the **set targetLength** instruction

>> use the drop down arrow and select the **crossHairStart** variable name
>> set the value in the **white circle** to **30** 


>> repeat to add another **set** for **targetDirection** with a value of **1** 

And also for 

>> - **targetDirection** with a value of **1**
- **crossHairRed** with a value of **100**
- **crossHairGreen** with a value of **0**
- **crossHairBlue** with a value of **100**

Also change the **set targetStart** value to **10**


``` blocks

let startStop = 0
let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetDirection = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
targetStart = 10
targetLength = 10
let crossHairStart = 30
targetDirection = 1
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

    function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}

```


## Create a new fucntion 
to control the crossHair LEDs


### In a clear space on the screen

add an ``||V Advanced||``  ``||Functions||``   ``||functions.make()||`` 
``||a Function||`` block

> Type in the function name **crossHair**  
in the white box to the right of the word **function** 
replacing the words **do something** 

Then add the function parameters by clicking on the ``||Number||`` button
and typing in the parameter names.

Create the parameters below

> - **crossHairStart** 
- **crossHairLength** 
- **crossHairRed** 
- **crossHairGreen** 
- **crossHairBlue** 
                                                         

click **Done** and then move the new function to a clear space
on the screen.

> if you have placed the function before creating the parameters, 
right click on the function block and select **Edit Function** 
to modify it and add the parameters.


### Add some code instructions
inside the ``||crossHair||`` function add the following..


 > a **Neopixel** ``||neopixel.set.range()||``

 After the word **set** in the set range instruction,

 > use the drop down **v** arrow to select the variable **range** 
 if it is not already showing.

 After the word **to** in the set range instruction, 

>  use the drop down **v** arrow to select the variable **strip** 
 if it is not already showing.


 ### In the blue boarder
of the **crossHair** function block

 > click and drag the **crossHairtStart** red oval and drop it to the **set range** instruction
 onto the **white circle** after the word **from**

 > Do the same for the **crossHairLength** word dropping it onto 
 the right hand **white circle**

### Below this add a                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              

  ``||Neopixel||`` ``||neopixel.strip.show.color()||`` 

  > Use the left end drop down arrow **v** to change 
the variable from **strip** to **range**


From the **Neopixel More** menu find a 

 **Neopixel**  **....more**   **red green blue** instruction

> and drag it to dock over the word **red** with an arrow next to it.

 ### In the blue boarder
of the **crossHair** function block

 > click and drag the **crossHairRed** red oval and drop it to the 
 **white circle** after the word red.
 
 >> Do the same for the **green** and **blue** values.

### When it is called, or activated, 
this code sends the colour instruction to a block of LED pixels. 
The pixels are defined by the values in the variables 
that the function is sent when it is called. 

These variables are called the function's parameters.

``` blocks

function crossHair (crossHairStart: number, crossHairLength: number, crossHairRed: number, crossHairGreen: number, crossHairBlue: number) {
    range = strip.range(crossHairStart, crossHairLength)
    range.showColor(neopixel.rgb(crossHairRed, crossHairGreen, crossHairBlue))
}

let crossHairBlue = 0
let crossHairGreen = 0
let crossHairRed = 0
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
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)


```

## Change the buttons and activate the new function. 
Find the **on button A pressed** function block. 

> Add a  ``||Variables.variables change()||`` instruction 

>> and drop it below the **strip clear** instruction 

In the **change** instruction use the **v** arrow to select the 
variable **targetStart** 

> and check the value is the **white circle** is **1**


### Repeat the same for button B 
find the **on button B pressed** block 

> Add a  ``||Variables.variables change()||`` instruction 

>> and drop it below the **strip clear** instruction 

In the **change** instruction use the **v** arrow to select the 
variable **targetStart** 

> and check the value is the **white circle** is **-1**

### Find the forever block
Inside the block, add an **V Advanced**  **Functions**   ``||Functions.call()||`` 
**Your Functions**  **call crossHair** instruction. 

> Dragging and dropping it into the **forever** block.

### Add the function parameter variables.

In the  ``||Variables.variables set()||`` menu

> From the **Your Variables** section, drag a copy of the variable **crossHairStart** onto the first **white circle** 
after the words **call crossHair**

> in the second **white circle** enter the value **2**

From the **Your Variables** section, do the same 
for the other white cirlces in the order 

> - **crossHairRed** 
- **crossHairGreen** 
- **crossHairBlue**



### This additional code changes the variable targetStart and calls the function crossHair. 
> This variable tells the **target** set of LEDs how far up the strip to start. 

> It is changed each time the button is pressed.

> The **call** activates the function which tells the LEDs 
where the **crossHair** set of LEDs is located. 
It is activated continuosly from 
within the **forever** block, which runs all of the time.








``` blocks

input.onButtonPressed(Button.A, function () {
    startStop = 1
    strip.clear()
    targetStart += 1
    targetRed = 50
    targetGreen = 50
    targetBlue = 0
})

input.onButtonPressed(Button.B, function () {
    startStop = 1
    strip.clear()
    targetStart += -1
    targetRed = 0
    targetGreen = 100
    targetBlue = 100
})

basic.forever(function () {
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
    crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
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

let crossHairBlue = 0
let crossHairGreen = 0
let crossHairRed = 0
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
basic.pause(200)
basic.showLeds(`
    . . . . #
    . . . # .
    # . # . .
    . # . . .
    . . . . .
    `)


```

## Set the colours and try it out 
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
    targetStart += targetDirection * -1
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})


input.onButtonPressed(Button.B, function () {
    strip.clear()
    targetStart += targetDirection
    targetRed = randint(0, 255)
    targetGreen = randint(0, 255)
    targetBlue = randint(0, 255)
})


basic.forever(function () {
    target(targetStart, targetLength, targetRed, targetGreen, targetBlue)
    crossHair(crossHairStart, 2, crossHairRed, crossHairGreen, crossHairBlue)
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



input.onButtonPressed(Button.AB, function () {
    strip.clear()
    targetRed = 0
    targetGreen = 0
    targetBlue = 0
    targetLength = 10
    targetStart = 10
    basic.pause(200)
    basic.showLeds(`
        . . . . #
        . . . # .
        # . # . .
        . # . . .
        . . . . .
        `)
})

let range: neopixel.Strip = null
let targetBlue = 0
let targetGreen = 0
let targetRed = 0
let targetDirection = 0
let targetLength = 0
let targetStart = 0
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 61, NeoPixelMode.RGBW)
strip.setBrightness(50)
strip.clear()
strip.show()
targetStart = 10
targetLength = 10
let crossHairStart = 30
targetDirection = 1
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


```


## Making the target block move on its own. 
.

### Add a new variable
to start and stop the movement. 

> Make a variable by selecting  ``||Variables.make a variable()||``

> and clicking on the **Make a Variable...** black box

> give it the name **startStop**


### Set up the variable 
In the code find the **on start** block.

Add a  ``||Variables.variables set()||`` instruction

> and place it in the **on start** block below the **strip clear** instruction

>> use the drop down arrow and select the **startStop** variable name 
if it is not already selected 
>> set the value in the **white circle** to **0** 





### Find the forever block
and add some logic instructions


> by selecting a  ``||logic.if()||`` instruction
and dropping it inside, at the top of the **forever** block 

> select a ``||logic.if then else()||`` instruction
and dropping it inside the **if** instruction

> select another  ``||logic.if()||`` instruction
and dropping it inside the **else** part of the **if else** instruction

>> this creates a *nested* set of *if* instructions.


> select a ``||logic.compare 0 = v 0 ||`` instruction 
>> This is three up from the bottom of the list. Not the last one. 
Note that the compare instructions have vee shaped ends.  

>> drop this into the box the same shape at the top of the first 
**if** instruction 
and then do the same for the **if else** instruction 
and the lower **if**.


### Set up the compare instructions 
From the ``||Variables.your variables()||`` menu pick 
the **startStop** red oval and drop it onto the left hand 
**white circle** at the top of the top **if** compare = instruction 

> For the middle and lower **if** compare = instructions 
do the same for both dropping a **targetStart** variable red oval 
into the left hand **white circle**.

>> use the drop down arrows **v** to change each of the compare instructions 
and set the right hand circles as below 
- **startStop = 0** 
- **targetStart < 1** 
- **targetStart > 59** 


### Add the action if the logic is true 
place a **Variables** ``||Variables.set()||`` instruction 
inside each of the **if** instructions below the compare instructions. 

> use the drop down **v** to select the **targetDirection** variable 
and change the right hand value to **1** in the top **if** 
and **-1** in the lower **if** 


### to complete the block 
place a **Variables** ``||Variables.change()||`` instruction 
just above the **call target** instruction 

> and drop in  a **targetDirection** variable **red oval** onto 
the right hand **white circle** 

Add a ``||basic.pause||`` at the very bottom of the instructions 
and set it to **100** ms 


### This code 
 Tests to see if the start of the LED block is at zero, 
the lower end of the LED strip, or at 60, the far end of the strip. 
And changes the **targetDirection** variable to keep it within the strip.


``` blocks

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

function crossHair (crossHairStart: number, crossHairLength: number, crossHairRed: number, crossHairGreen: number, crossHairBlue: number) {
    range = strip.range(crossHairStart, crossHairLength)
    range.showColor(neopixel.rgb(crossHairRed, crossHairGreen, crossHairBlue))
}
function target (targetStart: number, targetLength: number, targetRed: number, targetGreen: number, targetBlue: number) {
    strip.clear()
    range = strip.range(targetStart, targetLength)
    range.showColor(neopixel.rgb(targetRed, targetGreen, targetBlue))
}


``` 

## Add some movement to the crossHair pixels. 

Find the **on button A pressed** function block. 


In the **change** instruction use the **v** arrow to select the 
variable **crossHairStart** 

> and check the value is the **white circle** is **1**


Find the **on button B pressed** function block. 


In the **change** instruction use the **v** arrow to select the 
variable **crossHairStart** 

> and check the value is the **white circle** is **-1**



This code will move the crossHair each time a button is pressed.



``` blocks

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
let crossHairGreen = 0
let crossHairBlue = 100
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

Does it do what you expected?


...

``` blocks

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
let crossHairGreen = 0
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