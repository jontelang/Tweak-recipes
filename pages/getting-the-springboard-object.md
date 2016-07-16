# iOS compatability

iOS 6+ confirmed.

# Getting the Springboard object

You might want to declare the interface to get the sharedApplication from the UIApplication interface.

```objective-c
@interface SpringBoard : UIApplication
-(void)relaunchSpringBoard; // Respring
@end
```

Then you can do

```objective-c
SpringBoard *springboard = (SpringBoard*)[NSClassFromString(@"SpringBoard") sharedApplication];
[springboard relaunchSpringBoard];
```

Or

```objective-c
SpringBoard *springboard = (SpringBoard*)[%(SpringBoard) sharedApplication];
[springboard relaunchSpringBoard];
```

Or, this one requires your to include the obj/runtime or similar.

```objective-c
SpringBoard *springboard = (SpringBoard*)[objc_getClass("SpringBoard") sharedApplication];
[springboard relaunchSpringBoard];
```