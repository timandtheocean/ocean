# Decoding a sysex patch dump
We are going to decode a sysexpatch dump for a synth the Pioneer Toriaz AS-1. 
This is usefull if you want to setup an editor the Electra One to be bidirectional.
In otherwords the Elelctra One will be able to read all parameters so they are visible.

## Required Tools
We use Sendmidi and RecieveMIDI to communincate with the synth, available for all platforms 
- https://github.com/gbevin/SendMIDI 
- https://github.com/gbevin/ReceiveMIDI
- https://www.urbanspaceman.net/shared/MidiDumpCompare.htm.zip

*You can also use MidiOX on windows, this also has a compare function or whatever works for you. 

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

```  
system-exclusive hex 00 40 05 00 00 01 08 10 03 00 18 18 7F 7F 7F 7F 7F 00 7F 00 00 00 00 01 00 20 46 00 00 07 00 04 00 00 00
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
00 00 00 00 00 00 00 00 00 00 00 dec
```

If you did not recieve anything check the manual of your synth. Sometime sysex, or other midimessages need to be enabled specificly.
In case of the Toraiz is connected it via USB and needed to set usb as "sysex cable".

9. We need to find the header. The data bytes are comming after the header. To find out check the manual.
In my case **00 40 05 00 00 01 08 10 03** is the header. After the header we count the databytes 1st byte is byte 0
You either copy the HEX data without the header to the MidiDumpCompare tool or you copy the whole message but then you need to subtract the header bytes.

10. We now twist a know on the AS-1, Oscillator 2, Keyfollow from ON, to OFF, a simple boolian.
11. Send another patch request and paste the data in the MidiDumpCompare tool. Hit compare:
**Be carefull no remove trailing white spaces from the data** otherwise all bytes will mismatch. 
**Byte 0 is not detected properly in my case**

![image](https://user-images.githubusercontent.com/93200656/139408792-746c5e2f-5b4f-4f4e-8263-add56daea82c.png)

12. You see that **byte 14** is different it was **00** and is now **01** 
Oscillator 2, Keyfollow from ON = **00** hex, to OFF **01** hex
13.  In our template we need to know the parameterNumber because we want to assign the value found in the sysex dump here.
You can open your template on [[app.electra.one]] and you can see the parameterNumber there or what I did is to search ```OSC2 KEYFOLLOW``` in the ```.epr``` json template

```
"type":"nrpn",
"parameterNumber":11,
```
14. next we need to setup the patch section in our template. This can only be done directly in the json.
When you download your latest templates ```.epr``` file you can use online tools to pretty print the json data. Coppy all json data here: [[https://jsonformatter.curiousconcept.com/]] and copy it back to your template. It will make it easier to work with JSON.

15. In detail howto add the patch request / reponse: https://docs.electra.one/developers/sysexparser.html
But lets continue.  
We got the patch **request** message, the **header**, static bytes in the beginning of the patch. which never not change, the byte location of our parameter. and **parameterNumber** and **type** in our template.
Our template uses **"type":"nrpn"** set it to whatever midi message you send to control your synth ( perhaps **sysex**, **cc7** or **cc14** )

**"bitWidth":7** will work but we use only 1 bit so **"bitWidth":1** will also work for this case.
In our case it is not important as byte 14 is only used for 1 parameter which has a 1 bit range.

See here the patch section with 2 parameter in the rules.
The second is a bogus one but like this its easier to see how to add more. 

```json
"devices":[
      {
         "id":1,
         "name":"Pioneer Toraiz AS-1",
         "instrumentId":"toraizas1",
         "port":1,
         "channel":3,
         "patch":[
            {
               "request":[ "00", "40", "05", "00", "00", "01", "08", "10", "06" ],
               "responses":[
                  {
                     "header":[ "00", "40", "05", "00", "00", "01", "08", "10", "03" ],
                     "rules":[
			                     {
                           "type":"nrpn",
                           "parameterNumber":11,
                           "parameterBitPosition":0,
                           "byte":14,
                           "byteBitPosition":0,
                           "bitWidth":7
                        },
                        {
                           "type":"nrpn",
                           "parameterNumber":666,
                           "parameterBitPosition":0,
                           "byte":66,
                           "byteBitPosition":0,
                           "bitWidth":6
                        }
                     ]
                  }
               ]
            }
         ]
      }
   ],
```

16. when we have updated our template on windows stop ```RecieveMIDI``` as the driver is not multi client. 
Then send it to the electra one using Google Chrome [[https://app.electra.one/sandbox/]]
After testing close the sandbox tab in chrome so the driver is released and ```RecieveMIDI``` can be started again to capture more bits and bytes.

| attribute | function | notes |
|----------:|---------:|-------:|
| type | type of parameter | |
| parameterNumber | id of parameter | |
| parameterBitPosition | bit position within the parameter | |
| byte | position of the byte in the SysEx message | byte 0 is the first one after the header bytes | |
| byteBitPosition | bit position within the SysEx byte | |
| bitWidth | number of bits to be used | |


 

