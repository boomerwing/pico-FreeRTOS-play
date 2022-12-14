# RP2040-FreeRTOS try 1.0.0

This repo contains my base project for [FreeRTOS](https://freertos.org/) on the Raspberry Pi RP2040 microcontroller

## Project Structure

```
/FreeRTOS-PICO
|
|___/App-Keyer              // Source code for App-Keyer

|___/App-Shuffle            // Source code for App-Keyer

|___/Common                 // Source code common to applications
|
|___CMakeLists.txt          // Top-level project CMake config file
|___pico_sdk_import.cmake   // Raspberry Pi Pico SDK CMake import script
|
|___README.md
|___LICENSE.md
```

## Prerequisites

To use the code in this repo, your system must be set up for RP2040 C/C++ development. See [this blog post of "smittytone"](https://blog.smittytone.net/2021/02/02/program-raspberry-pi-pico-c-mac/) for setup details.

## Usage

1. Clone the repo: `git clone https://github.com/smittytone/RP2040-FreeRTOS`.
1. Enter the repo: `cd RP2040-FreeRTOS`.
1. Install the submodules: `git submodule update --init --recursive`.
1. Optionally, edit `CMakeLists.txt` and `/<Application>/CMakeLists.txt` to rename the project.
1. Optionally, manually configure the build process: `cmake -S . -B build/`.
1. Optionally, manually build the app: `cmake --build build`.
1. Connect your device so it’s ready for file transfer.
1. Install the app (I use the Drag and Drop process described in the pico-sdk documentation)

## The Apps

This repo includes a number of deployable apps. The project builds them all, sequentially. Exclude apps from the build process by commenting out their `add_subdirectory()` lines in the top-level `CMakeLists.txt`.

### App One: App-Keyer

This C app is a Morse Code CW Keyer used by Radio Amateurs to automatically transmit a repeated message in Morse Code. A number of messages can be stored and selected by switches.  The code shows three switches to select up to eight messages. A Seven Segment LED module shows the message number and two LED dots blink in response to the morse code being sent.

### App Two: App-Shuffle

This C app is a programming exercise to create a shuffle function. It can be set to shuffle any length character string (as shown it shuffles a complete Alphabet). It is controlled by two switches which are debounced in separate RTOS tasks. The output is displayed in the Minicom terminal App which is controlled by VT100 codes. The display shows how to use the switches to command the function.

### Common: Seven_seg.c

This code configures the Seven Segment LED module and displays the number (HEX or Decimal) sent to it.  My LED Module has two dots.  If your module has no dots or just one, you can use separate LEDs.


## Credits

This work has as its foundation the code provided by the smittytone/RP2040-FreeRTOS project.


## Copyright and Licences

Application source © 2022, Calvin McCarthy and licensed under the terms of the [MIT Licence](./LICENSE.md).

Application source © 2022, Tony Smith and licensed under the terms of the [MIT Licence](./LICENSE.md).

[FreeRTOS](https://freertos.org/) © 2021, Amazon Web Services, Inc. It is also licensed under the terms of the [MIT Licence](./LICENSE.md).

The [Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk) is © 2020, Raspberry Pi (Trading) Ltd. It is licensed under the terms of the [BSD 3-Clause "New" or "Revised" Licence](https://github.com/raspberrypi/pico-sdk/blob/master/LICENSE.TXT).
