# Address Based Wireless Device Selection Using 433 MHz RF

One transmitter selects one of four receivers over a 433 MHz radio link, using address codes set on HT12E and HT12D encoder and decoder ICs. No microcontroller and no programming is needed.

## 📌 Overview

A plain radio link carries a signal to every receiver within range, so every receiver responds to every signal unless the signal carries an address. This is often solved with microcontrollers, which need programming, extra components and software skills.

This project uses dedicated encoder and decoder ICs instead. The HT12E encoder attaches an address code, set by its address pins, to the data. All four HT12D decoders receive the signal, but only the decoder whose address pins match the encoder accepts the data and lights its LEDs. The other three ignore it. The address is fixed by wiring the address pins, so no programming is needed.

## 🎯 Objectives

* Transmit data wirelessly using a 433 MHz RF transmitter and receiver module
* Use one encoder IC at the transmitter to attach an address code to the data
* Use four decoder ICs at the receiver, each wired with its own address pin configuration
* Let only the decoder whose address matches accept and decode the data
* Show the decoded output on 20 LEDs, five for each decoder
* Demonstrate address based identification and control of devices without a wired connection

## ⚙️ How It Works

1. A channel button is pressed at the transmitter.
2. The HT12E attaches the address code, set by its address pins, to the data of the pressed button.
3. The RF transmitter sends the signal at 433 MHz.
4. The RF receiver passes the signal to all four HT12D decoders.
5. Each decoder compares the received address with its own address pin configuration.
6. The decoder whose address matches accepts the data. Its VT pin indicates a valid transmission and its LEDs glow to match the button pressed.
7. The other decoders do not accept the data.

**Transmitter unit:** four push buttons, the HT12E encoder IC and the 433 MHz RF transmitter module.

**Receiver unit:** the 433 MHz RF receiver module, four HT12D decoder ICs and 20 LEDs, with five LEDs on each decoder.

## 🔌 Addressing and IC Pins

Both ICs are 18 pin chips with eight address pins, A0 to A7. Each address pin is either connected to ground or left open, and the combination of the eight pins forms the address code. For a decoder to accept a signal, its address pins must be wired in the same arrangement as the encoder. Eight address pins allow up to 256 different address codes.

* **HT12E:** address pins A0 to A7, data inputs AD0 to AD3, TE (transmit enable), OSC1 and OSC2 (oscillator), and Output (serial data to the RF transmitter)
* **HT12D:** address pins A0 to A7, data outputs D0 to D3, Input (serial data from the RF receiver), OSC1 and OSC2 (oscillator), and VT (valid transmission)

## 🧰 Components Used

* Push buttons, 4
* HT12E encoder IC, 1
* 433 MHz RF transmitter module, 1
* 433 MHz RF receiver module, 1
* HT12D decoder ICs, 4
* LEDs, 20
* LM7805 voltage regulator IC for a regulated 5 V supply
* Resistors: 1 kilo ohm (20), 100 kilo ohm (20) and 1 mega ohm (1)
* Copper antennas for the RF modules
* Two 9 V batteries

**Build:** the transmitter circuit is built on a breadboard and the receiver circuit on a perforated board. Both are powered from 9 V batteries, and the LM7805 gives the regulated 5 V supply to the receiver.

## 📈 Results

The circuit was tested by changing the address pin configurations of the decoder ICs and transmitting signals with the RF encoder.

* The transmitter and receiver communicated wirelessly using 433 MHz RF signals.
* Each of the four decoders was identified by its address configuration.
* The LEDs of the matching decoder glowed when it received the transmitted signal, and the others stayed off.
* The range of RF communication was 100 metres with copper antennas. With suitable high gain antennas, the range can exceed 1 km.

The project successfully demonstrated wireless address matching using one RF encoder and four RF decoder ICs, with LEDs giving visual confirmation of the selected decoder.

## ✅ Advantages

* Selective wireless control of one receiver out of several on the same radio channel
* No microcontroller and no programming needed
* Low cost, using commonly available components
* Clear visual confirmation of the selected decoder
* Simple circuit that is easy to build and test
* Easy to expand, because eight address pins allow up to 256 address codes
* No wired connection between the transmitter and the receiver circuits

## 📚 References

1. Holtek Semiconductor Inc., HT12E 2^12 Series of Encoders, Datasheet
2. Holtek Semiconductor Inc., HT12D 2^12 Series of Decoders, Datasheet
3. LM7805 Three Terminal Positive Voltage Regulator, Datasheet

## 👤 Author

B Shyam Sunder
Electronics and Communication Engineering, SRM Institute of Science and Technology, Ramapuram
