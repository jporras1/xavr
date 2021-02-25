X-AVR
=====
### NOTE:
Use this in the case of setting up this development environment on a new computer.

**X-AVR** is an XCode template for generating `AVR C` projects.

Now the meta version: **X-AVR** is a python script which uses the installed `avr-gcc` and `avrdude` to generate and install an XCode `TemplateInfo.plist` file. This template can be used to create `AVR C` XCode projects with a `Makefile` to build and upload the program to an `AVR` chip.

*Notice*: This template does not generate projects in *the arduino language*. The generated project uses the `C` language and the `avr-libc` library.

For example, activating pin 13 on an arduino looks like this:

```C
DDRB |= _BV(PB5)
PORTB |= _BV(PB5)
```
# Prequisites

Using `homebrew` run the following commands:

```
brew install avrdude
brew tap osx-cross/homebrew-avr
brew install avr-gcc
```

# Usage

## Installation
Clone this repository or download the source zip somewhere in your mac and run `python setup.py` to generate and install the XCode project template.

The previous step need only be run once (or whenever you install a new `avr-gcc` version).

## After Installed
Once the template is installed, you should see an `xavr` entry in the new project wizard in XCode.

The wizard page lets you select the target MCU, its frequency and the programmer to be used to upload the program.

After the wizard is done, hit `Cmd+B` to build the project.

The project is created with the following targets:

* `All`: performs a clean build and uploads the generated hex to the target MCU
* `Build`: performs a clean build
* `Upload`: uploads the generated hex to the target MCU
* `Clean`: deletes the build artifcats
* `Index`: a *trick* target to get XCode autocompletion to work. You're not supposed to interact with this target

Also check [Using XCode for AVR C developement](http://jawher.me/2014/03/21/using-xcode-avr-c/) for more detailed instructions and screenshots.


# Credits
All credit goes to [jawher/xavr](https://github.com/jawher/xavr), this is just my simplified version to follow.

## Other Resources
This [site](https://jawher.me/using-xcode-avr-c/) gives a decent example on how to use the tool once it is installed. It is really old, but mostly still relevant.
