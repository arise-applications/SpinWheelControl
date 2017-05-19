# Spin Wheel Control v0.1.4

## Synopsis

Spin Wheel Control is an inertial spinning wheel UI control that allows selection of an item. It is written in the Swift programming language and to be used in iOS apps.

The code is a Swift derivation, port, and enhancement based loosely on the Objective-C "SMWheelControl" CocoaPod written by Cesare Rocchi and Simone Civetta found at https://cocoapods.org/pods/SMWheelControl.

Main languages and technologies used: Swift, UI Kit, Core Animation, CocoaPods, Xcode


## Installation 

To run this on your own machine: 

* Install Cocoapods on your machine, 

* Create a podfile in the project's root directory and add this line to that file:
'''
pod "SpinWheelControl"
'''

* Run pod install from the command line while inside your project's' root directory.

No extra configuration should be necessary to include this control in Swift projects.

To make this work in your Objective-C project:

* In your project's (not the target's) build settings, set the Defines Module flag to YES.

* Find your product module name by going to your target's (not the project's) build setting and search for Project Module Name.

* Add the SpinWheelControl files to your project.

* Import <productModuleName-Swift.h> in every Objective-C class you plan to use your Swift classes in. This file is created automatically by the compiler when you include Swift classes in an Objective-C project.


## Usage

Ensure the view controller containing the SpinWheelControl adheres to the SpinWheelControlDataSource and SpinWheelControlDelegate protocols:

```swift
class ViewController: UIViewController, SpinWheelControlDataSource, SpinWheelControlDelegate
```


Instantiate the UI control with a frame:

```swift
let frame = CGRect(x: 0, y: 0, width: self.view.frame.size.width, height: self.view.frame.size.width)

spinWheelControl = SpinWheelControl(frame: frame)
```


Add a target for the valueChanged event:

```swift
spinWheelControl.addTarget(self, action: #selector(spinWheelDidChangeValue), for: UIControlEvents.valueChanged)
```


Give the SpinWheelControl a data source:

```swift
spinWheelControl.dataSource = self

spinWheelControl.reloadData()
```


Set the SpinWheelControl's delegate:

```swift
spinWheelControl.delegate = self
```


Add the SpinWheelControl to your view:

```swift
self.view.addSubview(spinWheelControl)
```


### Data Source Methods

The following data source methods are available:

```swift
//Specify the number of wedges in the spin wheel by returning a positive value that is greater than 1

func numberOfWedgesInSpinWheel(spinWheel: SpinWheelControl) -> UInt

//Returns the SpinWheelWedge at the specified index of the SpinWheelControl

func wedgeForSliceAtIndex(index: UInt) -> SpinWheelWedge
```


### Delegate Methods


The following delegate methods are available:

```swift
//Triggered when the spin wheel control has come to rest after spinning.

func spinWheelDidEndDecelerating(spinWheel: SpinWheelControl)


//Triggered at various intervals. The variable radians describes how many radians the spin wheel control has moved since the last time this method was called.

func spinWheelDidRotateByRadians(radians: CGFloat)
```


## Author

Josh Henry

[Big Smash Software](http://www.bigsmashsoftware.com)

[Portfolio](http://www.joshhenry.info)

[LinkedIn](https://www.linkedin.com/in/joshdhenry)


## License
[BSD 3-Clause](http://opensource.org/licenses/BSD-3-Clause)
