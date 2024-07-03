# grumpy ZMK firmware

[Here](https://github.com/weteor/grumpy) you can find the hardware files.

## What is this?
This is my personal keymap for the grumpy keyboard.

The layout I use is bird from jcmkk3. [source](https://github.com/jcmkk3/bird-layout)

In this keymap I use: 
- something akin to callum style mods (though not exactly)
- slightly customized layer taps for non-home-row pinky keys (mostly inherited from kilipan's keymap, subject to change)
- tri-layer/conditional layer
- momentary layer on a combo
- combos with individual timeouts
- a simple implementation of a 'Linger Key' for the `qu/Qu` bigram, bound to a combo
- and potentially other idiosyncratic things which are nigh unavoidable on such small boards

## My modifications

This keymap firmware config is forked from kilipan, the changes are a consequence of personal preferences.
I've kept a lot of the custom behavior already present, modified some, and added others.

I prefer callum style mods to more common hold-tap (i.e. mod-tap) home row mods, but the ZMK `&sk` behavior doesn't behave in a way I'm used to from one shot mods from QMK.
In QMK, OSMs behave as normal mods when held, i.e. they don't get queued up when held. This isn't the case for sticky keys by default, and the most obvious solution that comes to mind is implementing a hold-tap that only triggers the `&sk` when the key is tapped, otherwise behaves as a normal mod. I haven't explored the potential solutions very thoroughly, so there might be even simpler solutions.

Other than that, I've implemented something called Linger Key by the Hands Down family of layouts creator. My starting point was the sch/Sch macro already present in kilipan's keymap.
Essentially, a linger key is supposed to output a macro that can also be shifted (which would make the first letter capital) when tapped, but only the first letter when held (which can also be shifted).
This can be achieved nicely with ZMK's hold-tap behavior. I've bound this to a combo on top row, middle and index finger (the usual position of Q on the bird layout).

## Keymap-drawer representation

Courtesy of [caksoylar's keymap-drawer](https://github.com/caksoylar/keymap-drawer) :)

![keymap_drawer_representation](./documentation/grumpy_keymap.svg?raw=true "Keymap representation")

## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [github desktop](https://desktop.github.com/))
- adjust the `.keymap` file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the keyboard to your PC, press reset and hold the boot key during reset
- the keyboard should now appear as a mass storage device
- drag'n'drop the `.uf2` file from the archive onto the storage device
