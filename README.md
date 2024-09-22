# Embedded System Homework Lab1: LED blinking and RTOS API

In this repository, the following problem (basic, optional) is solved. To examine the result, one should prepare [this STM32 board](https://www.st.com/en/evaluation-tools/b-l475e-iot01a.html) and the STM32CubeIDE with EGit extension.

## Problem 

### Basic
Press the button to trigger LED2 blinking (keep blinking in 5s with 1Hz frequency). The EXTI interrupt handler detects the button press and then inform Task_1 via a binary semaphore to blink LED.
LED2 blinks (keep blinking in 2s with 10Hz frequency) automatically every 10s. The timer interrupt handler detects the timeup event and then inform Task_2 via another binary semaphore to blink LED.
Thus, there are two different types of blinking for one LED. When one of blinking procedure is ongoing, the other should wait for blinking to avoid interference. Namely, you need to use a mutex to protect blinking procedures.

### Optional
The difference from the basic problem is, you need to identify the long button press event (don't release the button over 1s). When detecting such event, Task_1 executes another blinking procedure (keep blinking in 5s with 10Hz frequency). There are two types of blinking chosen by Task_1 according to long press or normal press, so Task_1 should be informed by distinguishable messages from a queue rather than a binary semaphore.
(In this problem, you might need to resolve the button bounce issue.)
