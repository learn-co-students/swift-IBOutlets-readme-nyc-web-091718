# IBOutlets & IBActions

![Drawing](http://i.imgur.com/fD3ROGh.png?1)
> Do, or do not. There is no 'try'. -[Yoda](https://en.wikipedia.org/wiki/Yoda)

## Overview

In this lesson, we'll dive into the way in which graphical components of our application are tied to our Swift code, so that we can make our app respond to user actions like button presses.


## Learning Objectives

* Connect the View Controller in the storyboard file to the `ViewController.swift` file
* Locate and use the Assistant Editor
* Pull up the Assistant Editor using the hotkey Command + Option + Return
* Hide the Assistant Editor using the hotkey Command + Return
* Use Control + drag a Label/Button/View from the View Controller into their `ViewController.swift` file and name it

## Designing the Interface

To get started, open up the Xcode project distributed in this repo (it's at `IBOutletFun/IBOutletFun.xcodeproj`). Take a look at some of the files included in the project, particularly `Main.storyboard` and `ViewController.swift`. Like before, you will design your app's interface in `Main.storyboard`, and write the code that makes it work in `ViewController.swift`.

Right now, both these files are mostly empty. Let's start with designing the interface (you have to start somewhere, after all). Click once on `Main.storyboard` in the file listing to display it in the Interface Builder editor.

Like before, your app first needs a _view controller_. Drag a new view controller from the object library onto `Main.storyboard`'s canvas.

![Create](http://i.imgur.com/s2uXjgG.png)

The first thing you need to do is associate this view controller with the code you are about to write. The Xcode project already includes a file called `ViewController.swift`, which defines one class, `ViewController` (creative names, huh?). You can associate your new view controller with this class in the Attribute Inspector. First, make sure that **View Controller** is selected in the object listing.

![Viewfsdfroller](http://i.imgur.com/8BWrwGk.png)

Then bring up the Attributes Inspector. The section at the top is called **Custom Class**. This is where you will associate the view controller with its code. In the **Class** text box, start typing in `ViewController`. After you type a few letters (probably just `V`, in fact), the full name `ViewController`, will autocomplete. You can press Return to accept the autocompletion, or type out `ViewController` yourself. Either way, make sure `ViewController` is entered in the **Class** text field.

![ViewCofdsfsfnftroller](http://i.imgur.com/KB0hrwK.png)

You can click the grey arrow next to **ViewController** in the **Class** text field, which should open `ViewController.swift` in an editor pane. This will show that you have correctly set up the association between the view controller in `Main.storyboard` and the code that backs it. You're not quite ready to write any code yet, though, so switch back to `Main.storyboard`, either by hitting the back button in Xcode's navigate ribbon, or by clicking on `Main.storyboard` in the file listing.

Ultimately, you want your interface to look like this:

![HellofsWorld](http://i.imgur.com/7dIlWD3.png)

What parts does that interface consist of?

1. A view controller and main view (which you just added)
2. Three buttons marked **Hello World**, **Goodbye World**, and **Unicorn!**
3. A label, simply marked **Label**.

Not a lot of stuff there, but it's enough to get a thorough demonstrate of how to create an app that responds to user input. Let's get started on laying it out!

First, let's put the label on the main view. Find a label in the object library (remember, you can filter the library by a search string) and drop it in the middle of the interface.

![Addsssalabel](http://i.imgur.com/1psWNLs.png)

Resize it horizontally so it takes up most of the width of the view. In its Attributes Inspector, change its text alignment so the text is centered.

![Centeressext](http://i.imgur.com/4AsP26P.png)

Build and run your application. Did you see your interface with the label in the simulator?

Probably not! You probably got this error message in the debugger console instead:

![Errofsr](http://i.imgur.com/HeEEfT6.png)

What does that error mean?

Think back to your previous lessons. Are you forgetting something? Maybe…an _initial view controller?_ That's right—you haven't set up the initial view controller yet! Remember, every iOS application has to have one—and only one—initial view controller.

Quit the simulator and go back to Xcode. Select the view controller in your Interface Builder editor. In the Attributes Inspector, make sure **Is Initial View Controller** is checked.

![Issacntroller](http://i.imgur.com/tTCT7Le.png)

Now try building and running your application again. This time it should work flawlessly, but there's still not much to it. Before you write some code, though, finish up with the layout of the interface.

You need to add three buttons to the interface. Like labels, buttons can be dragged from the object library (hint: filter by "button"). You can double-click on the button to change its text. Change the buttons so they read **Hello World**, **Goodbye **World**, and **Unicorn!**. When you're done, your interface should be complete, and look like this:

![Helloggnld](http://i.imgur.com/7dIlWD3.png)

Build and run your application again. Press on some of the buttons. They respond like buttons—you're clearly pressing them—but they don't do anything yet! Ideally, we want them to change the text label below so pressing each of them changes the label to a unique string of text, but right now they just sit there, inert, accepting presses but doing nothing in return. That's about to change.

## And Now, the Code

Now it's time for the part you've patiently been waiting for: Writing the code that will actually make your app _do_ something.

But first, a primer on two important concepts: _IB outlets_ and _IB actions_.

Swift code is associated with graphical interface elements through the use of outlets and actions. An _IB Outlet_ (short for _Interface Builder outlet_) is a _graphical_ component that your code _links_ to. An _IB action_ is the reverse: It is a method in your _code_ that a _graphical component_ links to. It is through these connections that your graphical components are able to do something in response to user input.

### IB Outlets

First things first: You want button presses to change the text label in your interface. Your code first has to know that the text label even exists and link to it. It does this by creating an _IB outlet_ between the view controller code and the text label.

The first thing you want to do is display your view's code alongside the view itself. Xcode offers a handy way of doing this: the Assistant Editor. Do you see the two sets of buttons in the top right corner of the Xcode toolbar? The second one from the left, marked with two circles, allows you to open up the Assistant Editor.

![Assistantlllon](http://i.imgur.com/2qWZ7O2.png)

This will open up `ViewController.swift` in an editor pane. If you're on a small screen, you might want to put the editor on the _bottom_ instead of the left hand side, which you can do by selecting **Assistant Editors on Bottom** from the Assistant Editor button.

![Assistanabcdttom](http://i.imgur.com/yVnwlft.png)

After you've opened the editor, you should see `ViewController.swift` at the bottom of your screen.

![vcSwiswft](http://i.imgur.com/7GE7yzd.png)

This will make it a lot easier to enter new code and show the relationship between the code and your user interface.

Back to outlets. You first need to make sure that your code is aware that a text label exists, and link to it (so it can eventually change the text on the label).

First, you need to declare an outlet in `ViewController.swift`. Add this code to the `ViewController` class definition:

```swift
@IBOutlet weak var textDisplay: UILabel!
```

When you're done, the definition of `ViewController` will look like this:

```swift
class ViewController: UIViewController {

    @IBOutlet weak var textDisplay: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
}
```

What's going on with this code? First, you told the Swift compiler that you were declaring an IB Outlet, using the `@IBOutlet` directive. That looks a bit weird, and you haven't seen that before, but all it does is tells Swift, "Hey, I'm about to declare a variable that has a connection to a user interface component." You then declared the variable to be `weak`. You'll learn more about `weak` variables later; for now, you just have to know that all IB outlets are `weak` variables. Finally, you declared a variable (using the `var` keyword) named `textDisplay`. This variable is of type `UILabel!`, because `UILabel`s are exciting. (Actually, it has to do with Swift's `Optional` types, which you'll learn about in a future lesson. For now, just know that IB outlets' types always end in an exclamation point `!`.)

Now it's time to connect this outlet to its user interface component! Xcode makes this really, really easy. You see how there's a little grey dot next to the line of code you just added? That's how you connect your `textDisplay` variable to a user interface component. Click and hold your cursor on the little dot, then drag your cursor to the label (helpfully marked **Label**) in your user interface. (If you're on a small screen, you may have to scroll the Interface Builder pane down a bit in order to see the label.) Drag the cursor over the label. Once it is highlighted, release your mouse button. The connection has now been set up. You can confirm this by checking the dot next to the line of code you added: It should be filled in now, instead of empty.

![IBOutlefacnnection](http://i.imgur.com/AFIsExV.png)

In order to demonstrate this connection, change the label from the default ("Label") to "Zzz..." in the view controller's `viewDidLoad()` method. Add this line to the end of `viewDidLoad()`:

```swift
textDisplay.text = "Zzz..."
```

Your definition of `ViewController` should now look like this:

```swift
class ViewController: UIViewController {

    @IBOutlet weak var textDisplay: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()
        textDisplay.text = "Zzz..."
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
}
```

Build and run your application. Notice that the label now says "Zzz..." instead of "Label"—you used the IB outlet connection to change it in code!

Now, let's make the buttons do something cool.

### IB Actions

Consider the problem: You want your code to respond to button presses. You kind of know about these things called "IB actions", but you don't really know exactly what they are. How would you go about solving this problem? How would you link up user interface elements, like buttons, to code?

If you guessed "functions" or "methods", you're absolutely correct. An _IB action_ is nothing more than a method in your view controller class that is tied to a user interface element. When the user interacts with the element (pressing it, entering text, swiping it, and so forth), the method associated with that element is called.

Creating new IB actions in Xcode is easy (and kind of fun!). First, hold down Control and drag from the **Hello World** button in your interface to the `ViewController.swift` file. (Make sure you hold down Control and _drag_—if you just click, you will bring up a contextual menu.) Drag your mouse to the empty space _above_ (not _inside!_) the `viewDidLoad()` method, then release the mouse button.

![Dragablopion](http://i.imgur.com/YZd3oFu.png)

You will get a popup prompting you to set the type of the connection, and give it a name. Make sure the **Connection** type is set to **Action** (it is set to **Outlet** by default!) and change the **Name** to `helloWorld`, then click the **Connect** button.

![Createfrodoion](http://i.imgur.com/tnyhQ2f.png)

You'll see a new method in your `ViewController` definition:

```swift
@IBAction func helloWorld(_ sender: AnyObject) {
}
```

What's different about this compared to other method definitions you have seen? Namely, it is prefixed with the `@IBAction` directive. This tells the Swift compiler that this method is an Interface Builder action—it is connected to a view component (in this case, the **Hello World** button). You'll also see a little grey circle in the gutter next to this method definition, signifying that it is a connected action.

Now let's write some code to make that method _do_ something.

Remember that this method is called when the button is pressed. You want to change the label to say "Hello, world!" instead of "Label" or "Zzz...". You can change the text by adding this line to the body of `helloWorld(sender:)`:

```swift
textDisplay.text = "Hello, world!"
```

Let's add a `print()` call so you can see when this method is called, too:

```swift
print("Pressed Hello World button")
```

Now your complete definition of `ViewController` should look like this:

```swift
class ViewController: UIViewController {

    @IBOutlet weak var textDisplay: UILabel!

    @IBAction func helloWorld(_ sender: AnyObject) {
        print("Pressed Hello World button")
        textDisplay.text = "Hello, world!"
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        textDisplay.text = "Zzz..."
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
}
```

Build and run your application. Press the **Hello World** button and see what happens. Did the label's text change to "Hello, world!"? It should have! You should also see "Pressed Hello World button" logged to the debug console.

![HelloWorflacdld](http://i.imgur.com/CeuPVfD.png)

If you pressed any of the other buttons, you should see that they didn't do anything. Why not? Right now, they're not connected to any IB actions. Time to wire them up! Add a new IB action from the **Goodbye World** button to your `ViewController.swift` file. Name it `goodbyeWorld`. Don't forget to set the **Connection** type to **Action**!

![Addsamwisetion](http://i.imgur.com/D1zDwng.png)

Once again, add a `print()` statement to the body of `goodbyeWorld(sender:)`, then change the label text to "Goodbye, world!".

You can build and run the app again, but you still have a problem: The **Unicorn!** button is not hooked up yet. Can you figure out how to do that yourself?

Here's a hint: Add another IB action the same way you did before. Control-drag from the **Unicorn!** button to `ViewController.swift`, and create an action named `unicorn`. As before, the method body should include a `print()` statement to demonstrate that it has been called. It should also change the text of the label to the unicorn emoji (yes, you can use emoji in Swift strings).

Now your complete definition of `ViewController` should look like this:

**NOTE**: Due to the inability to include emoji's in this readme, where you see the letter x below, replace that with the unicorn emoji.

```swift
class ViewController: UIViewController {

    @IBOutlet weak var textDisplay: UILabel!

    @IBAction func helloWorld(_ sender: AnyObject) {
        print("Pressed Hello World button")
        textDisplay.text = "Hello, world!"
    }

    @IBAction func goodbyeWorld(_ sender: AnyObject) {
        print("Pressed Goodbye World button")
        textDisplay.text = "Goodbye, world!"
    }

    @IBAction func unicorn(_ sender: AnyObject) {
        print("Pressed Unicorn! button")
        textDisplay.text = "x"
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        textDisplay.text = "Zzz..."
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }
}
```

Build and run your app again. Does the text label change appropriately based on the buttons you pressed?

You should also see some output in Xcode's debug console:

![Debug output](http://i.imgur.com/8y9Rt7P.png)

Congratulations! You've written your first app that actually _does something_ in response to user input. Relish in your newfound knowledge.

<a href='https://learn.co/lessons/OutletTargetAction' data-visibility='hidden'>View this lesson on Learn.co</a>

<p class='util--hide'>View <a href='https://learn.co/lessons/swift-IBOutlets-readme'>IBOutlets & IBActions</a> on Learn.co and start learning to code for free.</p>
