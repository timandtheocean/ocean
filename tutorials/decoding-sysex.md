# Decoding a sysex patch dump
We are going to decode a sysexpatch dump for a synth the Pioneer Toriaz AS-1. 
This is usefull if you want to setup an editor the Electra One to be bidirectional.
In otherwords the Elelctra One will be able to read all parameters so they are visible.

## Required Tools
We use Sendmidi and RecieveMIDI to communincate with the synth, available for all platforms 
- https://github.com/gbevin/SendMIDI 
- https://github.com/gbevin/ReceiveMIDI
- https://www.urbanspaceman.net/shared/MidiDumpCompare.htm.zip

*You can also use MidiOX on windows, this also has a compare function. 

## Required info
- Manual of the synth ( sometimes there is a seperate sysex manual )
- We need a "patch request message" when we send it to the synth it will return a patch in sysex format

## setting up SendMIDI and RecieveMIDI
1. download the releases for your platform and extract it
2. run ```SendMIDI dev list``` to find your *midi output device*
3. run ```RecieveMIDI dev list``` to find your *midi input device*
4. start capturing midi sysexdata ```receivemidi.exe dev "Toraiz AS-1" syx``` ( leave out syx if you want to see all midi messages )
5. Initialize a patch on your synth
6. send a patch request sysex message ```sendmidi.exe dev "Toraiz AS-1" syx hex 00 40 05 00 00 01 08 10 06```  ( leave out F0 ... F7 )
7. open the '''MidiDumpCompare.htm''' in Google chrome
8. If all is setup correctly we should have recieved a patch dump which looks something like this:

```system-exclusive hex 00 40 05 00 00 01 08 10 03 00 18 18 7F 7F 7F 7F 7F 00 7F 00 00 00 00 01 00 20 46 00 00 07 00 04 00 00 00
00 00 00 00 00 7F 00 00 7F 7F 7F 7F 7F 00 00 00 00 00 00 00 7F 00 00 28 00 00 00 00 00 40 00 40 64 0A 64 40 00 00 08 03 03 00
06 0B 00 00 00 00 01 00 00 00 00 00 00 7F 00 00 00 00 00 00 00 7F 7F 00 00 00 00 00 00 00 00 00 78 00 02 00 00 00 06 00 00 07
00 7F 00 7F 7F 7F 7F 7F 7F 00 00 06 00 42 61 73 69 63 00 20 50 72 6F 67 72 61 00 6D 20 20 20 20 20 20 30 20 64 3C 40 7F 7F 3C
02 43 7F 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 00 3C
3C 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 00 3C 3C 3C 3C 3C 3C 3C 78 3C 3C 3C 7F 7F 7F 7F 07 7F 7F 7F 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 dec```

If you did not recieve anything check the manual of your synth. Sometime sysex, or other midimessages need to be enabled specificly.
In case of the Toraiz is connected it via USB and needed to set usb as "sysex cable".

9. We need to find the header. The data bytes are comming after the header. To find out check the manual.
In my case **00 40 05 00 00 01 08 10 03** is the header. After the header we count the databytes 1st byte is byte 0
You either copy the HEX data without the header to the MidiDumpCompare tool or you copy the whole message but then you need to subtract the header bytes.

10. We now twist a know on the AS-1, Oscillator 2, Keyfollow from ON, to OFF, a simple boolian.
11. Send another patch request and paste the data in the MidiDumpCompare tool. Hit compare:

![image](https://user-images.githubusercontent.com/93200656/139408792-746c5e2f-5b4f-4f4e-8263-add56daea82c.png)

12. You see that **byte 14** is different it was **00** and is now **01** 




 

