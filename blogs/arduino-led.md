---
layout: default
title: Arduino Programming Problems LED changing patterns
---

[« Home](https://jedsadasrijunpoe.github.io/)

<h1>Arduino Programming Problems LED changing patterns</h1>

# Problems 1)
- Write Arduino C/C++ programs that implement the following LED changing patterns (A, B, C, D).
- Use the Wokwi Simulator first to test your code and then verify the correctness using real hardware.

## LED changing pattern: A
- Step 1. Initially, only one LED (at index=0) is ON, and the rest of the LEDs are OFF.  
- Step 2. The position of the ON LED should be moved to the next in a circular manner in a fixed time interval and then repeat Step 2.

<img src='https://github.com/JedsadaSrijunpoe/JedsadaSrijunpoe.github.io/blob/main/images/arduino-led/led-pattern-a.gif?raw=true' alt='LED changing pattern A' />

```c++
#if defined(ESP32)
const int LED_PINS[] = {23,22,32,33,25,26,27,14,12,13};
#else
const int LED_PINS[] = {2,3,4,5,6,7,8,9,10,11};
#endif

const int NUM_LEDS = sizeof(LED_PINS)/sizeof(int);

void setup() {
  for ( int i=0; i < NUM_LEDS; i++ ) {
    // set the direction of the i-th LED pin
    pinMode( LED_PINS[i], OUTPUT ); 
    // turn on the first LED (i=0) and the rest off. 
    digitalWrite( LED_PINS[i], (i==0) ? HIGH : LOW );
  }
}

void loop() {
  for ( int i=0; i < NUM_LEDS; i++) {
    //turn on the i LED for 500 ms then turn off
    digitalWrite( LED_PINS[i], HIGH);
    delay(500);
    digitalWrite( LED_PINS[i], LOW);
  }
}
```
In this code, we have defined GPIO pins for Arduino Nano and ESP32 DevKit V1 by using `LED_PINS` array
If it's ESP32 DevKit V1, we would use these pins
```c++
const int LED_PINS[] = {23,22,32,33,25,26,27,14,12,13};
```
If it's Arduino Nano, we would use these pins
```c++
const int LED_PINS[] = {2,3,4,5,6,7,8,9,10,11};
```
I use ESP32 Devkit V1 for this pattern

![Circuit LED pattern A](/images/arduino-led/led-a.png)
Wokwi Simulator for this pattern: https://wokwi.com/projects/342300798050370131

## LED changing pattern: B
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the LEDs one by one with a time delay, starting at index=0 until all LEDs are ON.  
- Step 3. If all LEDs are ON, turn off LEDs one by one starting at index=n-1, where n is the total number of LEDs, until all LEDs are OFF, and repeat Steps 2-3.

<img src='https://github.com/JedsadaSrijunpoe/JedsadaSrijunpoe.github.io/blob/main/images/arduino-led/led-pattern-b.gif?raw=true' alt='LED changing pattern B' />

```c++
#if defined(ESP32)
const int LED_PINS[] = {23,22,32,33,25,26,27,14,12,13};
#else
const int LED_PINS[] = {2,3,4,5,6,7,8,9,10,11};
#endif

const int NUM_LEDS = sizeof(LED_PINS)/sizeof(int);

void setup() {
  for ( int i=0; i < NUM_LEDS; i++ ) {
    // set the direction of the i-th LED pin
    pinMode( LED_PINS[i], OUTPUT ); 
    // turn on the first LED (i=0) and the rest off. 
    digitalWrite( LED_PINS[i], (i==0) ? HIGH : LOW );
  }
}

void loop() {
  for ( int i=0; i < NUM_LEDS; i++) {
    // turn on the LEDs one by one with a time delay,
    // starting at index=0 until all LEDs are ON.
    digitalWrite( LED_PINS[i], HIGH);
    delay(100);
  }
  for ( int j=0; j < NUM_LEDS; j++) {
    // turn off the LEDs one by one starting at index=n-1,
    // where n is the total number of LEDs, until all LEDs are OFF
    digitalWrite(LED_PINS[NUM_LEDS-1-j], LOW);
    delay(100);
  }
}
```
In this pattern, I use Arduino Nano.
![Circuit LED pattern B](/images/arduino-led/led-b.png)
Wokwi Simulator for this pattern: https://wokwi.com/projects/342247407381119572
## LED changing pattern: C
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the first LED by increasing the duty cycle of the PWM signal driving the LED, until the LED is fully ON.  
- Step 3. Repeat Step 2 with the next LED until all LEDs are fully ON.  
- Step 4. If all LEDs are ON, turn off LEDs one-by-one by decreasing the duty cycles of the PWM signals until all LEDs are OFF and repeat Steps 2-4.

<img src='https://github.com/JedsadaSrijunpoe/JedsadaSrijunpoe.github.io/blob/main/images/arduino-led/led-pattern-c.gif?raw=true' alt='LED changing pattern C' />

```c++
const int LED_PINS[] = {5,18,19,21};
const int NUM_LEDS   = sizeof(LED_PINS)/sizeof(int);

#define OFF (HIGH) // active-low LED

void setup() {
  for ( int i=0; i < NUM_LEDS; i++ ) {
    // set the direction of the i-th LED pin
    pinMode( LED_PINS[i], OUTPUT ); 
    digitalWrite( LED_PINS[i], OFF );
  }
}

const int PWM_RESOLUTION = 8;
const int PWM_FREQ = 1000;
const int DUTY_MAX = (1 << PWM_RESOLUTION);

void loop() {
  // turn on LEDs one by one by increasing the duty cycle of the PWM
  for ( int i=0; i < NUM_LEDS; i++ ) {
      ledcSetup( i /*channel*/, PWM_FREQ, PWM_RESOLUTION );
      ledcAttachPin( LED_PINS[i] /*pin*/, i /*channel*/ );
      for ( int x=0; x <= DUTY_MAX; x++ ) {
         ledcWrite( i, DUTY_MAX-x );
         delay(1);
      }
  }
  // turn off LEDs one by one by decreasing the duty cycle of the PWM
  for ( int i=0; i < NUM_LEDS; i++ ) {
      ledcSetup( i /*channel*/, PWM_FREQ, PWM_RESOLUTION );
      ledcAttachPin( LED_PINS[i] /*pin*/, i /*channel*/ );
      for ( int x=0; x <= DUTY_MAX; x++ ) {
         ledcWrite( i, x );
         delay(1);
      }
      ledcDetachPin( LED_PINS[i] ); 
      digitalWrite( LED_PINS[i], OFF );
  }
}
```
![Circuit LED pattern C](/images/arduino-led/led-c.png)
[How to use LEDC API for ESP32](https://espressif-docs.readthedocs-hosted.com/projects/arduino-esp32/en/latest/api/ledc.html)
Wokwi Simulator for this pattern: https://wokwi.com/projects/342312038793478740
## LED changing pattern: D
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the first 4 LEDs using PWM signals, each with different duty cycles (e.g. 100%, 50%, 25%, 10%), and the rest of the LEDs are OFF.  
- Step 3. Move the positions of ON LEDs to the left by one position in a circular manner and repeat Step 3.

<img src='https://github.com/JedsadaSrijunpoe/JedsadaSrijunpoe.github.io/blob/main/images/arduino-led/led-pattern-d.gif?raw=true' alt='LED changing pattern D' />

```c++
const int LED_PINS[] = {21, 19, 18, 5, 4, 2, 15, 22};
const int NUM_LEDS   = sizeof(LED_PINS) / sizeof(int);

#define OFF (HIGH) // active-low LED

void setup() {
  for ( int i = 0; i < NUM_LEDS; i++ ) {
    // set the direction of the i-th LED pin
    pinMode( LED_PINS[i], OUTPUT );
    digitalWrite( LED_PINS[i], OFF );
  }
}

const int PWM_RESOLUTION = 8;
const int PWM_FREQ = 1000;
const int DUTY_MAX = (1 << PWM_RESOLUTION);
// duty cycles 10%, 25%, 50%, 100%
const float DUTY_CYCLES[] = {0.1,0.25,0.5,1};

void loop() {
  // starting at index=0, and move the positions of ON LEDs to the left by one
  for ( int i=0; i < NUM_LEDS; i++) {
    // turn on 4 LEDs, each with different duty cycles
    for ( int j=0; j < 4; j++) {
      ledcSetup( j, PWM_FREQ, PWM_RESOLUTION );
      ledcAttachPin( LED_PINS[(i+j)%NUM_LEDS], j );
      ledcWrite( j, (1 - DUTY_CYCLES[j])*DUTY_MAX );
    }
    delay(100);
    // turn off the 4 LEDs
    for ( int j=0; j < 4; j++) {
      ledcDetachPin( LED_PINS[(i+j)%NUM_LEDS] );
      digitalWrite( LED_PINS[(i+j)%NUM_LEDS], OFF );
    }
  }
}
```
![Circuit LED pattern D](/images/arduino-led/led-d.png)
Wokwi Simulator for this pattern: https://wokwi.com/projects/343517173322351187

# Problem 2)
- Reimplement LED changing patterns A and B using the Pin C++ class.

## LED changing pattern: A