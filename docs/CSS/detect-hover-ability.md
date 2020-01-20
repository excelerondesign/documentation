## Detecting hover abilities for responsiveness

_[Guide](https://css-tricks.com/touch-devices-not-judged-size/)_

This is useful for determining if a device is even capable of viewing a `:hover` state.

Before you choose one method in the guide, I recommend that you also read the Rare Interaction Capabilities: The any-pointer and any-hover Features section, since some devices are are iffy in how they register.

##### Support:

[caniuse](https://caniuse.com/#feat=css-media-interaction) mentions that FireFox support is lacking.
This is remedied as follows:

```css
@supports (-moz-animation: foo) {
	/** fallback for firefox **/
}
```
