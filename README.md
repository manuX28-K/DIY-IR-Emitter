# DIY-IR-Emitter
A custom built, DIY themed IR Transmitter with decent range specially made for Bruce Firmware.

![BruceIRPreview](https://github.com/manuX28-K/DIY-IR-Emitter/blob/main/DIYirPreview.jpg)


## The Idea ...

...is very simple, I have tried multiple solutions offered by various people and various manufacturers for IR Transmitting, but none seem to give the optimal range in order for me to use with the Bruce Firmware ( credit is due to all the amazing falks who develop Bruce ). So I did some research on how to develop a custom IR Emitter, thus finally decided to create one with various easy to find components. This solution offers about 7 to 10ft of range on a closed environment where there's less sunlight available ( while most of the other IR emitters only offer about a range of <5ft ). 


## The components you need 👇🏻

1. TSAL6400 5mm IR LED
2. 2N2222 NPN Transistor
3. 47 ohm Resistor
4. 1K ohm Resistor
5. 6.3v 100uf capacitor ( + 0.1uf ceremic capacitor if possible )
6. 10cm female to female/male jumpers ( need to be cut in half )

## How to assemble?

Fairly easy to do, schematic is provided below. With that, all you need is patience and a bit of soldering work to get it up and running.

![CircuitDiagram](https://github.com/manuX28-K/DIY-IR-Emitter/blob/main/CircuitDiagram.png)
![CircuitDiagram2](https://github.com/manuX28-K/DIY-IR-Emitter/blob/main/Diagram2.jpg)

ASCII re-presentation of the circuit diagram 👇🏻👇🏻
```

3.3V ----[47Ω]---->| (IR LED)
                         |
                      Collector (C) - 2N2222
                      Base (B) <- [1kΩ] <- ESP GPIO (IR_TX)
                      Emitter (E) -> GND
(100µF cap across 3.3V and GND)

```
NOTE : 3.3v --> 47ohm resistor --> ( + ) side of the led, ( - ) side of the led goes to the collector pin of the 2N2222. DO NOT MESS UP these two wirings or you can easily fry your transistor 🤒

### Important information before soldering;

1. The resistor which is marked as 1K, should be connected with the data pin ( in this case GPIO 17 as the TX pin specified in Bruce Firmware ) of the esp32 S3.
2. 47ohm resistor gives about 100 mAh of peak pulses ( is it the correct term... ), allowing safe yet powerful transmitting capabilities.
3. Using a 6.3v 100uf capacitor is not must, but it helps with smoothing the voltage spikes being in the process, thus allowing better performance.
4. The shorter the wires better. ( The longer the length of wires, the lower the peak mAh will get due to resistence. )
5. This is tested under regular conditions ( meaning, at my house on my own TV ), so you could expect the same if not better results on a more controlled environment.

## Thank you for testing this out 🩷

Always keep in mind, I do not encourage any illegal activity using this DIY solution. Always use on the devices that you own or have permission to test on, thus keep it legal and safe. Thank you for testing this project...peace 🫡

![InAction](https://github.com/manuX28-K/DIY-IR-Emitter/blob/main/InAction.jpg)


### Inspiration and further readings :
>> ![Tasmota's IR Solution ](https://tasmota.github.io/docs/IR-Remote/#related-projects)
>> ![Issue with the poor range : Reddit](https://www.reddit.com/r/AskElectronics/comments/183mhh6/increase_voltage_power_for_ir_led_powered_by_33v/)
