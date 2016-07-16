# iOS compatability

iOS 6+ confirmed.

# Getting the Springboard object

You might want to declare the interface to get the sharedApplication from the UIApplication interface.

	@interface SpringBoard : UIApplication
	-(void)relaunchSpringBoard; // Respring
	@end

Then you can do

    SpringBoard *springboard = (SpringBoard*)[NSClassFromString(@"SpringBoard") sharedApplication];
    [springboard relaunchSpringBoard];

Or

    SpringBoard *springboard = (SpringBoard*)[%(SpringBoard) sharedApplication];
    [springboard relaunchSpringBoard];

Or, this one requires your to include the obj/runtime or similar.

    SpringBoard *springboard = (SpringBoard*)[objc_getClass("SpringBoard") sharedApplication];
    [springboard relaunchSpringBoard];