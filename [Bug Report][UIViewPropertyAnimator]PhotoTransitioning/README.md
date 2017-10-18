# Note

This is a modified project that was submitted to Apple earlier today to help identify a potential bug in UIViewPropertyAnimator API.

The `TransitionAnimator` has been observed to end too late where `FrameAnimator` has already finished 5 seconds earlier.
The `TransitionAnimator`, which was then resumed by `continueAnimation(withTimingParameters:durationFactor:)`, was first paused by a user touch through a call to `pauseAnimation`. If, on some conditions, where users try to interrupt the animation multiple times back and forth, the duration of the resumed animation may exceeded the expectation.

## Apple documentation:

**durationFactor**
A multiplying factor to apply to the animation’s original duration. The value of this parameter is multiplied by the original duration value to obtain the new duration for the animations.

https://developer.apple.com/documentation/uikit/uiviewpropertyanimator/1648371-continueanimation