# iOS compatability

iOS 6+ confirmed.

# Getting / Setting volume

```objective-c
// Interface might be needed
@interface VolumeControl
+ (id)sharedVolumeControl;
- (void)setMediaVolume:(float)arg1;
- (float)getMediaVolume;
@end

// And usage
float volume = [[%c(VolumeControl) sharedVolumeControl] getMediaVolume];
[[%c(VolumeControl) sharedVolumeControl] setMediaVolume:0.1f];
```