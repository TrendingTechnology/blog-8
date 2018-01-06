---
date: 2017-10-12T13:33:46-04:00
title: "QMK Firmware on the Whitefox"
slug: /qmk-firmware-on-the-whitefox/
description: |-
  How to install QMK firmware on your WhiteFox keyboard.
categories:
  - Development
tags:
  - QMK
  - Mechanical Keyboards
  - Homebrew
  - GitHub
  - Make
  - WhiteFox
draft: true
---

I think we all know how great the WhiteFox is, what I didn't know is that I was
going to become kind of addicted to mechanical keyboards after using it.

I'm writing this post because this keyboard became somewhat an obsession to me.
I switched and customized the key mappings quite a lot in the first few months,
and although the KLL firmware with the configurator is great and I had no
trouble with it I was always drawn to the TMK firmware.

Before buying the WhiteFox I was thinking about getting the Infinity 60%
keyboard because of its Open Source characteristics, and with it the TMK
firmware. Luckily the WhiteFox compatibility for it was added to TMK and QMK,
and I wanted to try it.

## Installing the environment

There are a hand full of dependencies needed to be able to compile your QMK
firmware. If you are in macOS, go ahead and install the following, else follow
the [QMK build tools docs][qmk-build-tools]:

You'll need Homebrew and a few taps:

    brew tap osx-cross/avr
    brew tap caskroom/cask/gcc-arm-embedded

Then install:

    brew install avr-gcc dfu-programer
    brew cask install gcc-arm-embedded

That's all you need environment wise.

Installation is a slow process

## Building the Firmware

To build the firmware you'll need to clone the repo, or if you plan to make a
custom layout for your keyboard fork it and clone it.

Once you finish cloning the repo, install all the `submodules`

    make git-submodule

Once you are done, you should be ready to go.

Now try to build the default WhiteFox layout, if you succeed you are ready to
go.

Every command you'll need to run from now on is within `Make`

    make whitefox-default

Will compile the default WhiteFox keyboard layout.

    make whitefox-default-clean

Will clean the build only for this keyboard

Once you are ready to flash something to your keyboard:

    make whitefox-default-dfu-util

This command will use the previously installed `dfu-programer` package and flash
the keyboard. Remember to put your keyboard in DFU mode by pressing the button
located on the bottom.

## Creating a custom layout



---

This concludes how to flash a WhiteFox keyboard with the QMK Firmware.

[qmk-build-tools]: https://docs.qmk.fm/getting_started_build_tools.html
