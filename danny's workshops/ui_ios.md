## UI Development on iOS using Cocoa
This workshop will go over the basics for working with Cocoa in Xcode to easily build dynamic, visually-driven applications (although really, what good mobile applications aren't visually-driven?).

#### What you'll use
Interface coding is slightly more complicated in iOS than in android. You'll basically need to forge some sort of harmony between your class files (managed by the Xcode editor) and your interface files (managed by interface builder). For the most part, you can control the main communication between the code and the screen through two things: 
- IBOutlets = Cocoa objects that represent something you would find in an interface (e.g. a button) - these aren't really necessary on android, as you can reference interface objects by ID
- IBActions = Functions that occurs in response to some sort of interface action (e.g. a button press) - this same functionality is achieved via a listener interface on Android

##### Class Files
What's cool about the class files is that you can freely program IBActions and IBOutlets just as you would any other variable or method in Swift or Objective-C. These just need a special annotation.
```
/**
 ** Objective-C
 **/

//MyInterface.h
@interface MyInterface : UIViewController
{
    IBOutlet UILabel *myLabel;
}
-(IBAction)action:(id)sender;
@end

//MyInterface.m
@implementation MyInterface
-(IBAction)action:(id)sender{
    [myLabel setText:@"Hello, World!"];
}
@end

/**
 ** Swift
 **/

@IBOutlet var myLabel: UILabel!
@IBAction func myAction(action: AnyObject){
    myLabel.text = "Hello, World!"
}
```

Note that the Apple [documentation]() holds all of the different Interface objects, usually denoted by UI in the front (e.g. UITableView) - this should be your bible when it comes to using native iOS interface objects - Android has a similar reference guide - most of these interface objects fall under the android.app package.

##### Interface Builder 
Interface Builder is a drag-and-drop editor for iOS views. You just need to assign a view controller or another object to a corresponding class file. Then, through the inspector panel, you can assign IBActions and IBOutlets. 

##### A note about storyboards
Interface Builder uses a scene management system called Storyboards. They are designed to make app flow design and visualization easy. The best way to understand how they work is with practice. That being said, keep the following in mind: 
    - Storyboards are sets of scenes
    - Scenes are containers consisting of different views
    - Segues are transitions between scenes. 
		- You should network your Segues in Interface Builder, but setup actual segue code (e.g. passing objects or information from one scene to another) in the view controller's segue methods (e.g. prepareForSegue)
		- Segues should have identifiers (names)
    - IBActions and IBObjects can only be set within a scene - I cannot link a button press in one scene to an action in another - unless... I use the responder chain - but I'll leave that as a homework assignment for you to look up


#### Key Takeaways
Everything you need to know is on the [apple docs](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIKit_Framework/index.html#//apple_ref/doc/uid/TP40006955). Keep in mind that making your applications come to life requires a careful combination of Cocoa knowledge and comfort with Objective-C or Swift. Make good use of Interface Builder, but don't apply changes you don't understand!  
