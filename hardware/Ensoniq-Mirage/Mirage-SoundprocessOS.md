# Sysex for the Ensoniq Mirage running Trtons Soundprocess OS

The sysex patch mapping is clearly documented in the Sound Process OS manaual.
Some data needs to be send in 2 4bit nibbles otheres don't

We use Sendmidi and RecieveMIDI to communincate with the synth
https://github.com/gbevin/SendMIDI
https://github.com/gbevin/ReceiveMIDI

1. Set Mirage in CC mode 'Computer Control' only then it responds to sysex

```
F0 00 00 23 01 02 F7
```

parameter request message for parameter hex:55 decimal 85, Filter Frequency
```
.\sendmidi.exe dev "Electra Controller" hex syx 00 00 23 01 03 55
```

response, after the parameter we see the value 00 00
```
.\receivemidi.exe dev "Electra Controller"
system-exclusive hex 00 00 23 01 43 55 00 00 dec
```
The mirage give another response message.
Here are the most important codes, they can be found in the soundprocess manual

| response code | description |
| ------:| -----:| 
| 00 | system ok |
| 01 | no computer control, see 1. how to set the Mirage to Computer control|
| 02 | undefined error |
| 03 | Qualifier over range |
| 04 | Qualifier under range |
| 05 | DATA over range |
| 06 | DATA underrange |



Sysex Patch Map and control ID

| Offset | Bytes | Hex mask   | Bin mask            | Bits | Description |
| ------:| -----:| :--------- | :------------------ | ----:| ----------- |
|      1 |     3 | `7F 7F 7F` | `01111111 01111111 01111111` | 3x 8 | Manufacturer ID |
|      9 |     1 | `7F`       | `01111111         ` |    8 | Patch number |
|     13 |     2 | `03 7C`    | `00000011 01111100` |    7 | Portamento Time |
