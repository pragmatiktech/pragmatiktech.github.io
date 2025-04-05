---
title: "Concurrency with Goroutines"
subtitle: "Doing multiple things at once."
summary: "Using goroutines to run functions concurrently."
date: 2022-07-10
author: Charath Ranganathan
categories:
  - Embedded Systems
  - TinyGo
image: /static/images/embedded/concurrency.jpg
order: 1
---

![](/static/images/embedded/concurrency.jpg)

Let us modify the simple blink program from our earlier [tutorial](/embedded/blinking-an-led.html) to run multiple tasks simultaneously. This is what we call *concurrency*.

Go has a number of primitives to help make programmers' lives easier when they create concurrent programs. In this tutorial, we will look at one of them, namely *Goroutines*.

{{< video https://youtu.be/q_6CoBZ0y_Q >}}

## The Program

The aim of our program is to do the following two things at once:

1. Blink the onboard LED twice a second.
2. Print the phrase "hello concurrently" to the serial (UART) port.

We modify the `blink.go` program from the earlier [tutorial](/embedded/blinking-an-led.html) to add:

1. A function (named `printHello`) that prints "hello concurrently" in an infinite loop.
2. A goroutine that spawns this function so that it runs concurrent to the main thread that is blinking the LED.

```go
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
		
	go printHello()
	
	for {
		led.High()
		time.Sleep(500 * time.Millisecond)
		led.Low()
		time.Sleep(500 * time.Millisecond)
	}
}

func printHello() {
	for {
		println("hello concurrently")
		time.Sleep(time.Second)
	}
}
```

## Testing the Program

Ensure that your serial console is set up as described in my earlier [tutorial](/embedded/setting-up-tinygo.html#optional-enable-serial-debugging) on setting up the Pico for serial debugging.

Flash the program to your pico:

```bash
% tinygo flash -target=pico concurrentblink.go
```

You should see the onboard LED blinking, while the phrase "hello concurrently" is printed every second in the serial monitor.

## References

- Rob Pike's [presentation](https://www.youtube.com/watch?v=tIrVLcUq4xE) on "Concurrency is not parallelism".