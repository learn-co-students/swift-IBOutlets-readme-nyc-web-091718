# IBOutlets (IB = Interface Builder)

<img src="http://cdn2.hubspot.net/hubfs/326641/yoda.jpg" alt="Drawing" style="width: 200px;"/>  
> Do, or do not. There is no 'try'.

## Learning Objectives - The student should be able to..

* Explain that the files they will write their code in within Xcode will be the .swift files they see in the Project Navigator.
* Connect the View Controller in the storyboard file to the ViewController.swift file.
* Locate and use the Assistant Editor
* Pull up the Assistant Editor using the hotkey, command + option + return.
* Hide the Assistant Editor using the hotkey, command + return.
* control + drag a Label/Button/View from the View Controller into their ViewController.swift file and name it. They should know the proper naming convention, similar to how they've been naming their variables (lower camel case)

## What the student can do at this point 

* More stuff

## Outline / Notes

*  Explain to the student that writing their code in a .swift file within Xcode is identical to how they wrote their code within a Playground file. In fact, they actually were writing their code in a .swift file when working with the playground file.
* Be thorough with screenshots and an explanation as to how they setup the Class of their View Controller to the ViewController.swift file.
* When selecting any of the UI elements that are located in their View. Explain how they can use the Attributes inspector to change the background color, font (if applicable).
* If you like, you can have them either follow along with you through screenshots or have them open an Xcode project (which is included) that makes them follow along. I think I'm more inclined to have them follow along with you in an Xcode file. I've included the Xcode file to this repo. (Auto Layout & Size Classes have been disabled)
* Walk them through dragging a View Controller onto the canvas. In doing so, have them drag one label to the middle of the View and run the app. In running the app, they should see that the simulator is showing a black screen (where's our label?!). They were taught in a prior reading that they should look to set the Initial View Controller in the Attributes inspector, so after they run the app, remind them that they have to do this.
* Walk them through creating something like this (show them this screenshot as well!) Not using Auto Layout:
![Hello World](http://i.imgur.com/7dIlWD3.png)
* After having them create this, have them run the app and tap the buttons. They can see obviously that they are selecting these buttons BUT nothing is happening. We want actionable things to occur when these buttons are tapped. We want to display text to the user of our app where it states Label (just leaving it as Label is boring). This is a fundmanetal thing in making iOS apps, someone taps something and then something else happens. The "something else happens" is where we come in! We build functions (similar to how we did in prior readings/labs). These functions dictate what occurs on screen (and off screen). But how do we do that? After posing that question, then go into detail how they hook it up to a View Controller. We need a place where we could write code associated with these visual elements, where do we do that? In our ViewController.swift file.

<a href='https://learn.co/lessons/OutletTargetAction' data-visibility='hidden'>View this lesson on Learn.co</a>
