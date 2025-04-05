---
title: "Blinking an LED with TinyGo"
subtitle: "Your first program."
summary: "In this tutorial, we look at what it takes to create the simplest program of all - one that blinks the onboard LED on the Raspberry Pi Pico."
date: 2022-07-04
author: Charath Ranganathan
categories:
  - Embedded Systems
  - TinyGo
image: /static/images/embedded/leds.jpg
order: 1
---
![](/static/images/embedded/leds.jpg)

# Blinking an LED with TinyGo

{{< video https://youtu.be/B-6GsoEg0Lw >}}

## The Program

The [program](https://github.com/pragmatiktech/tinygo-tutorial/blob/master/blink/blink.go) itself is simple - about 15 lines of code.

```go
// blink.go

package main

import (
		"machine"
		"time"
)

func main() {
		led := machine.LED
		led.Configure(machine.PinConfig{
		Mode: machine.PinOutput,
		})
		
		for {
			led.High()
			time.Sleep(500 * time.Millisecond)
			led.Low()
			time.Sleep(500 * time.Millisecond)
		}
}
```

## Basic Steps to Interact with GPIO

The basic steps for interacting with a General Purpose Input-Output (GPIO) pin on the Pico are the same:

1. Import the `machine` package.
2. Create a variable that is an instance of the GPIO pin.
3. Configure the instance.
4. Loop while doing something with the pin.

Let us examine each of these steps in detail.

### Import the `machine` Package

```go
import (
		"machine"
		... // other imports
)
```

The `machine` package provides an abstraction in Go to the underlying capabilities of the microcontroller target. It also defines some
constants that make it easier when referring to the facilities of the microcontroller in Go. As an example, consider the `machine.LED`
constant, which represents the onboard LED on the Pico.

### Create an Instance of the Pin

```go
led := machine.LED
```

Creating the variable and initializing it to an instance of `Pin` allows us to access the variable in other parts of the program.

Note that the pin is **not** configured yet. That needs to be done in the next step.

### Configure the `Pin` Instance

```go
led.Configure(machine.PinConfig{
		Mode: machine.PinOutput,
})
```

The `Configure` function takes an instance of a `type` called `PinConfig` as its input. The `PinConfig` type is defined as below:

```go
type PinConfig struct {
		Mode PinMode
}
```

The following `Mode`s are accepted:

```go
const (
		PinOutput PinMode = iota
		PinInput
		PinInputPulldown
		PinInputPullup
		PinAnalog
		PinUART
		PinPWM
		PinI2C
		PinSPI
)
```

Since we want the LED to blink, but are not concerned about its input, we configure the pin as a `PinOutput`.

### Loop

Once the GPIO pins are initialized and configured, we loop while performing a set of tasks. This is typical of any microcontroller (or
embedded) application. 

In the case of this trivial "blink" program, we turn the LED on and off periodically inside the loop. For the purposes of this program, we use a time of 500 milliseconds between turning the LED on, and turning it off.

```go
for {
	led.High()
	time.Sleep(500 * time.Millisecond)
	led.Low()
	time.Sleep(500 * time.Millisecond)
}
```

Outputting a `High` to the pin switches on the LED, while a `Low` turns it off. The `time.sleep` merely pauses the program so that the pin isn't toggled so frequently that the LED never appears to turn off.

## Summary

In this tutorial, we learnt to:

1. Initialize and configure a single GPIO pin using TinyGo.
2. Output binary high or low values to the pin.
3. Run our program endlessly.

## References

1. [GitHub](https://github.com/pragmatiktech/tinygo-tutorial/tree/master/blink)
2. [`machine` package reference for Pico](https://tinygo.org/docs/reference/microcontrollers/machine/pico/)