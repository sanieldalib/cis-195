# Tutorial 0: Environment Setup

Discuss this tutorial & get help on [Piazza](https://piazza.com/upenn/fall2019/cis195201/home).
Please leave feedback by creating a GitHub issue or by posting on Piazza.

**Expected Duration:** 10-15 minutes of engagement. 1+ hours of installing & updating software if required.


**Deadline:** Thursday, September 5th at **1:20pm**

- - - -

## Objectives
* Learn some vocabulary.
* Ensure your Xcode is set up correctly.
* Make sure you can run apps using the virtual iPhone simulator.
* Meet the _Playground_ — a “scratch pad“ to quickly experiment with Swift

## Vocab
* **iPhone** — a smartphone produced by Apple that runs the **iOS operating system**.
* **iOS** —  the operating system that runs all iPhones and iPads. It’s responsible for downloading and running apps, for making calls, for taking photos, and pretty much everything else.
* **Swift** — Apple’s modern programming language. It is the language used to make apps for iOS, watchOS, MacOS, and all other Apple platforms. The language is relatively new, so new versions (with different syntax!) come out frequently. For this reason, you should search **Swift 5** (the current version) whenever searching StackOverflow or Google.
* **Swift 5** — the just-released version of Swift, which we’ll use in this class.
* **UIKit** — Apple’s user interface development kit, used on iOS. This is how you **interact** with iOS. You’ll spend most of this class learning UIKit development.
* **Xcode** — an IDE (integrated development environment) provided by Apple. This is the iOS equivalent of Java’s Eclipse editor. It allows you to write and compile Swift, and also provides a lot of niceties (autocompletion! Type checking!).
* **Xcode Simulator** — a full iPhone simulator built into Xcode. We’ll use this to quickly test iOS apps without needing an actual iPhone.

## Install Xcode
1. Make sure you are running **MacOS 10.14.3 or later**. If you are not, update your OS from the Mac App Store. This version is required for the version of Xcode we use. Not all Macs can run this version, check that yours can [with this list](http://osxdaily.com/2018/06/05/macos-mojave-compatible-macs-list/).
![](/tutorials/tutorial-0/assets/fig1.png?raw=true)
3. Go to the Mac App Store and install Xcode. If you have Xcode already, make sure it is updated to version **10.3**.
![](/tutorials/tutorial-0/assets/fig2.png?raw=true)
4. Launch Xcode. Accept any permissions, you may have to put in your password. Xcode will also ask to “Install Additional Required Components” — click yes.

If you made it this far, your environment should be set up for the semester. Next, we’ll get started with Xcode playgrounds.

## Xcode Playgrounds
> “Playground - noun: a place where people can play”  

Playgrounds are miniature testing environments for the Swift language. They allow you to quickly try out code and see results — without making a full app! Many of our tutorials will use Playgrounds.

#### Do the following:
- Open Xcode.
- Click “Get started with a playground” in the left menu.
- Name the new playground `<YOUR_NAME>_tutorial-0` and save it in your new `tutorials` folder.

Great! You should now see a Playgrounds file with some boilerplate code:
![](/tutorials/tutorial-0/assets/fig3.png?raw=true)
1. This is the code editor. Code goes here! Click the **play** button to compile and run code.
2. This is a “status panel” — when you initialize a variable, it will show you the value of that variable. This will also show you useful debugging info, like how many times each line of code is run.
3. This is the output console — errors and print statements are sent here.

#### Do the following:
- Erase the line beginning with `var str = "Hello...`
- Write a comment: `// Tutorial 0`
- Make constants for your name, favorite emoji, and penn id (replace the <...>):
```
let name = "<YOUR NAME>"
let emoji = "<EMOJI>"
let pennId = <PENNID>
```
- Add a line to print out your constants:
```
print("Hello World \(emoji) My name is \(name) and my pennId is \(pennId)")
```
- Click the play button to compile and run.

Your playground should look like this:
![](/tutorials/tutorial-0/assets/fig4.png?raw=true)

Congrats! You just ran your first line of Swift 🎉🎉🎉

**DON’T FORGET:** Submit `tutorial-0.playground` on Canvas before you continue with Tutorial 1.


