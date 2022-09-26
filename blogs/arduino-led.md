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
    digitalWrite( LED_PINS[i], HIGH);
    delay(500);
    digitalWrite( LED_PINS[i], LOW);
  }
}
```

![led a](/images/arduino-led/led-a.png)
## LED changing pattern: B
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the LEDs one by one with a time delay, starting at index=0 until all LEDs are ON.  
- Step 3. If all LEDs are ON, turn off LEDs one by one starting at index=n-1, where n is the total number of LEDs, until all LEDs are OFF, and repeat Steps 2-3.

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
    digitalWrite( LED_PINS[i], HIGH);
    delay(100);
  }
  for ( int j=0; j < NUM_LEDS; j++) {
    digitalWrite(LED_PINS[NUM_LEDS-1-j], LOW);
    delay(100);
  }
}
```
![led b](/images/arduino-led/led-b.png)
## LED changing pattern: C
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the first LED by increasing the duty cycle of the PWM signal driving the LED, until the LED is fully ON.  
- Step 3. Repeat Step 2 with the next LED until all LEDs are fully ON.  
- Step 4. If all LEDs are ON, turn off LEDs one-by-one by decreasing the duty cycles of the PWM signals until all LEDs are OFF and repeat Steps 2-4.

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
  for ( int i=0; i < NUM_LEDS; i++ ) {
      ledcSetup( i /*channel*/, PWM_FREQ, PWM_RESOLUTION );
      ledcAttachPin( LED_PINS[i] /*pin*/, i /*channel*/ );
      for ( int x=0; x <= DUTY_MAX; x++ ) {
         ledcWrite( i, DUTY_MAX-x );
         delay(1);
      }
  }
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
![led c](/images/arduino-led/led-c.png)
## LED changing pattern: D
- Step 1. Initially, all LEDs are OFF.  
- Step 2. Turn on the first 4 LEDs using PWM signals, each with different duty cycles (e.g. 100%, 50%, 25%, 10%), and the rest of the LEDs are OFF.  
- Step 3. Move the positions of ON LEDs to the left by one position in a circular manner and repeat Step 3.

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
const float DUTY_CYCLES[] = {0.1,0.25,0.5,1};

void loop() {
  for ( int i=0; i < NUM_LEDS; i++) {
    for ( int j=0; j < 4; j++) {
      ledcSetup( j, PWM_FREQ, PWM_RESOLUTION );
      ledcAttachPin( LED_PINS[(i+j)%NUM_LEDS], j );
      ledcWrite( j, (1 - DUTY_CYCLES[j])*DUTY_MAX );
    }
    delay(100);
    for ( int j=0; j < 4; j++) {
      ledcDetachPin( LED_PINS[(i+j)%NUM_LEDS] );
      digitalWrite( LED_PINS[(i+j)%NUM_LEDS], OFF );
    }
  }
}
```
![led d](/images/arduino-led/led-d.png)

# Problem 2)
- Reimplement LED changing patterns A and B using the Pin C++ class.

## LED changing pattern: A