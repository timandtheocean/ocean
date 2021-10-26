# Pioneer As-1 SYSEX

## SysEx data sent by the Bass Station II

By default, the Bass Station II send 154 bytes. However, a patch (.syx file) may be smaller.
    
- **Offset**: index from the start of the SysEx data. First byte (0xF0) has offset=0.
- **Bytes**: number of bytes to consider for this parameter
- **Mask**: mask to apply to the above bytes to get the bits relative to the parameter
- **Bits**: how many bits form the value

| Offset | Bytes | Hex mask   | Bin mask            | Bits | Description |
| ------:| -----:| :--------- | :------------------ | ----:| ----------- |
|      1 |     3 | `7F 7F 7F` | `01111111 01111111 01111111` | 3x 8 | Manufacturer ID |
|      9 |     1 | `7F`       | `01111111         ` |    8 | Patch number |
|     13 |     2 | `03 7C`    | `00000011 01111100` |    7 | Portamento Time |
|     15 |     1 | `7E   `    | `01111110         ` |    7 | ? |
|     16 |     1 | `7F   `    | `01111111         ` |    7 | Osc Pitch Bend Range |
|     18 |     1 | `40   `    | `01000000         ` |    1 | Osc 1-2 Sync |
|     19 |     1 | `60   `    | `01100000         ` |    2 | Osc 1 Waveform |
|     19 |     2 | `0F 70`    | `00001111 01110000` |    7 | Osc 1 Manual PW |
|     20 |     2 | `07 78`    | `00000111 01111000` |    7 | Osc 1 Range |
|     21 |     2 | `07 7C`    | `00000111 01111100` |    8 | Osc 1 Coarse |
|     22 |     2 | `03 7E`    | `00000011 01111110` |    8 | Osc 1 Fine |
|     24 |     1 | `03   `    | `00000011         ` |    2 | Osc 2 Waveform |
|     25 |     2 | `3F 40`    | `00111111 01000000` |    7 | Osc 2 Manual PW |
|     26 |     2 | `1F 60`    | `00011111 01100000` |    7 | Osc 2 Range |
|     27 |     2 | `1F 70`    | `00011111 01110000` |    8 | Osc 2 Coarse |
|     28 |     2 | `0F 78`    | `00001111 01111000` |    8 | Osc 2 Fine |
|     36 |     1 | `30   `    | `00110000         ` |    2 | Sub Osc Wave |
|     37 |     1 | `08   `    | `00001000         ` |    1 | Sub Osc Oct |
|     37 |     2 | `07 7C`    | `00000111 01111100` |    8 | Mixer Osc 1 Level |
|     38 |     2 | `03 7E`    | `00000011 01111110` |    8 | Mixer Osc 2 Level |
|     39 |     2 | `01 7F`    | `00000001 01111111` |    8 | Mixer Sub Osc Level |
|     41 |     2 | `7F 40`    | `01111111 01000000` |    8 | Mixer Noise Level |
|     42 |     2 | `3F 60`    | `00111111 01100000` |    8 | Mixer Ring Mod Level |
