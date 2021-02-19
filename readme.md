## WARNING: These PCBs are largely untested, and have been uploaded for reviewing, and initial orders. ORDER AT YOUR OWN RISK. There are no guarantees that it will work, or that these designs will be supported with a case in the future.
## BOARD VERSIONS:
# Circut-Teensy32: Original small board for copper tape pads
# Circut-Teensy32-Full-Board-upwards: Full PCB with upward firing WS2812 LEDs. JLC can assemble. - NOT TESTED
# Circut-Teensy32-Full-Board-side: Full PCB with sideways firing SK6812 LEDs. JLC CANNOT assemble. - NOT TESTED
# Circut-Teensy32-Full-Board-separate: Full PCB with slots cut for a separate LED board. There are no LEDs on the board itself. JLC can assemble. - NOT TESTED
# Addon-LED-Board: Addon board for the above board. Has WS2812 LEDs, and slots into the main board for sideways firing. JLC PROBABLY can assemble, but only with the panelized version which combines 2 boards into one. - NOT TESTED

# All boards have through hole spots for edge connectors, the teensy, the USB port, and the Barrel Jack. The separate LED board uses 1X3 90 angled 2.54 pitch connectors to attatch to the main board.
# USB - USB4085-GF-A
# Connectors - JST-PH. 9 pin for the Air boards, 4 pin for the air LEDs
# Barrel Jack - any barrel jack with a standard 14x9mm footprint
# Teensy LC - Make sure you connect the data lines on the teens before soldering to the board. You can either drop a pin straight down, or run wires out to the pads in front of it.

# OpeNITHM

This repository contails files related to OpeNITHM.

Firmware, schematics, board layout, and CAD files are included in this repo. Please see the CAD directory for the original 3d printed version, or the v2-cad directory for the laser cut version. 

## List of Hardware

In the `CAD\STL` folder, you will find numerous parts that must be 3D printed.

Please check out [the wiki](https://github.com/veroxzik/OpeNITHM/wiki/File-Explanation) for more information.

| Part | Qty |
| --- |:---:|
| Center Frame | 1 |
| Right Frame | 1 |
| Left Frame | 1 |
| Key Dual 2.5mm **OR** Key Dual 3mm<sup>1</sup> | 16 |
| LED Support Peg | 16 |
| Sensor Rail | 2 |
| Sensor Spacer Left<sup>2</sup> | 1 |
| Sensor Base Left<sup>2</sup> **OR** Integrated Sensor Base Left<sup>2</sup> | 1 |
| Sensor Cover Left<sup>2</sup> | 1 |
| Integrated Frame Mount Left<sup>2,3</sup> | 1 |

**NOTES:** 
1. Use 2.5mm for 3/32" and 3mm for 1/8" acrylic. 
2. Print out mirrored version of these parts as well.
3. Only print the frame mount if you are using the integrated sensor.

The non-printed materials and hardware include:

| Part                                                                       | Qty |
| --- |:---:|
| 4-40 Flat Head Screw, length 3/16" to 5/16" will work **OR** M3 equivalent | 2   |
| Top Acrylic Plate<sup>1</sup> (472mm x 112mm)                              | 1   |
| Key Acrylic<sup>1</sup> (103.5mm x 26mm)                                   | 16  |
| Copper Tape, cut into rectangles 95mm x 26mm                               | 16  |

**NOTES:**
1. Use 2.5mm (3/32") **OR** 3mm (1/8") acrylic. Use the same acrylic for top plate and keys.

## List of Electronics

OpeNITHM is designed for the Teensy LC.

#### Why use Teensy and not Arduino?

The biggest reason is that Teensy has built in capacitive sensing, which is how OpeNITHM fuctions. You have to fake it on Arduino using very controlled analog reads, and it is nowhere near as sensitive. In my (VXZK's) experience, it was simply impossible to use an Arduino to do the capacitive sensing required for this project.

I chose the Teensy LC as it is the lowest cost Teensy model available with capacitive sensing. The firmware and PCB are designed for this board alone; significant modifications may be required for any other version.

There is an alternative build using an Arduino Pro Micro and 2 MPR121s as a branch in this repo, but it is not maintained and not recommended. You're on your own with that one!

### Teensy LC Build

Links are mostly suggestions (except the Teensy, which is only officially available through the PJRC site and authorized resellers).  
(VXZK: I've heard a lot of trouble regarding good quality IR leds and phototransistors, so I've included specific links to the ones I purchased and has worked well for me.)  

The links below also assume you want to socket your Teensy and multiplexers for later use. You can solder them directly, if you'd like.  
If you are going to solder your sensors directly to the PCB, it is not necessary buy the 0.1" Pin Header, Right Angle. Otherwise, include female 0.1" sockets for your sensors (commonly referred to as Dupont connectors).  

| Part | Link | Qty |
| --- | --- |:---:|
| Teensy LC | https://www.pjrc.com/store/teensylc.html | 1 |
| Teensy LC Breakout Board | this Github, Circuit-Teensy32 folder contains gerbers | 1 |
| 74HC4051 Multiplexer Breakout Board | [Aliexpress][1] | 4 |
| 0.1" Pin Header, 1 row, 40 pos | [Aliexpress (qty 10)][2] | 2 |
| 0.1" Pin Header, Right Angle, 2 row, 24 pos | [LCSC][3] | 2 |
| 0.1" Socket, Straight, 1 row, 14 pos | [LCSC][4] | 2 |
| 0.1" Socket, Straight, 1 row, 5 pos | [LCSC][5] | 2 |
| 0.1" Socket, Straight, 1 row, 11 pos | [LCSC][6] | 2 |
| 0.1" Socket, Straight, 1 row, 8 pos | [LCSC][7] | 2 |
| 51k ohm Resistor, 1/6W or 1/8W | LCSC or Aliexpress | 6 |
| 33 ohm Resistor, 1/4W, 1/6W, or 1/8W | LCSC or Aliexpress | 3 |
| 1m WS2812B RGB 5V LED Strip, 30LED Per Meter | [Aliexpress][8] | 1 |
| IR LED and Phototransistor | [Ebay (Qty 20 pairs)][9] | 6 |

[1]: https://www.aliexpress.com/item/32807771098.html
[2]: https://www.aliexpress.com/item/665534073.html
[3]: https://lcsc.com/product-detail/New-Arrivals_XFCN-PZ254R-12-24P_C492440.html
[4]: https://lcsc.com/product-detail/Pin-Header-Female-Header_Boom-Precision-Elec-Female-header-2-54-1-14P_C52711.html
[5]: https://lcsc.com/product-detail/Pin-Header-Female-Header_Boom-Precision-Elec-2-54mm-1-5p-Female-header_C50950.html
[6]: https://lcsc.com/product-detail/Pin-Header-Female-Header_Changjiang-Connectors-A2541HWV-11P_C225508.html
[7]: https://lcsc.com/product-detail/Pin-Header-Female-Header_Boom-Precision-Elec-2-54mm-1-8P-Straight-Female-header_C27438.html
[8]: https://www.aliexpress.com/item/2036819167.html
[9]: https://www.ebay.com/itm/40pcs-5mm-Infrared-LED-940nm-Emitter-Diode-and-IR-Receiver-Set/252235145540

## Board Revision and Sensors

As of 2020-07-17, the recommended board version is v2.1, which features inputs for 32 sensors. This best replicates the feeling of the arcade. Previous versions used 16 sensors. If you still wish to make a 16 key version, you can order the v2.1 but only populate two of the multiplexers. This is not really recommended.

## Installing on Teensy LC

**NOTE:** This firmware is *only* written to work for the Teensy LC. Do *not* use Teensy 2.0 or Teensy 3.x

Skip this section if you are using a Pro Micro.

Locate your `arduino` folder (usually `C:\Program Files (x86)\arduino`).

#### I have a fresh install of Teensyduino, or have never modified my USB profiles

Copy `Firmware/Teensy/boards.txt` to `arduino\hardware\teensy\avr\` and overwrite the existing.

Copy `Firmware/Teensy/teensy3` to `arduino\hardware\teensy\avr\cores\teensy3` and overwrite any conflicts.

Copy `Firmware/FastLED/WS2812Serial.cpp` and `Firmware/FastLED/WS2812Serial.h` to `arduino\hardware\teensy\avr\libraries\WS2812Serial` and overwrite the existing.

Copy `Firmware/FastLED/FastLED.cpp` and `Firmware/FastLED/FastLED.h` to `[My Documents]\Arduino\libraries\FastLED\` and overwrite the existing.

#### I am applying the changes manually

(It is easier to copy and paste from the files in `Firmware/Teensy` instead of through here, the below is just for reference.)

Add `usb_nkro.c` and `usb_nkro.h` to `arduino\hardware\teensy\avr\cores\teensy3`

In `arduino\hardware\teesny\avr\boards.txt` add lines 1175-1179

```c
1175    teensyLC.menu.usb.nkrokeyboard=NKRO Keyboard
1176    teensyLC.menu.usb.nkrokeyboard.build.usbtype=USB_NKRO
1177    teensyLC.menu.usb.nkrokeyboard.fake_serial=teensy_gateway
1178    teensyLC.menu.usb.serialnkrokeyboard=Serial + NKRO Keyboard
1179    teensyLC.menu.usb.serialnkrokeyboard.build.usbtype=USB_SERIAL_NKRO

In `arduino\hardware\teensy\avr\cores\teensy3\WProgram.h` add line 59

```c
58    #include "usb_joystick.h"
59    #include "usb_nkro.h"
60    #include "usb_midi.h"
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_inst.cpp` add lines 75-77

```c
72    usb_serial_class Serial;
73    #endif
74    
75    #ifdef NKRO_INTERFACE
76    usb_nkro_class Nkro;
77    #endif
78    
79    #else // F_CPU < 20 MHz
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_dev.h` add lines 93-98

```c
90    extern volatile uint8_t keyboard_leds;
91    #endif
92    
93    #ifdef NKRO_INTERFACE
94    extern uint8_t nkro_report_data[NKRO_SIZE];
95    extern uint8_t nkro_protocol;
96    extern uint8_t nkro_idle_config;
97    extern uint8_t nkro_idle_count;
98    #endif
99    
100   #ifdef MIDI_INTERFACE
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_desc.h` add lines 868-948

```c
866      #define ENDPOINT15_CONFIG	ENDPOINT_TRANSMIT_ONLY
867    
868    #elif defined(USB_NKRO)
869      #define VENDOR_ID		0x16C0
870      #define PRODUCT_ID		0x04D0
871      #define MANUFACTURER_NAME	{'T','e','e','n','s','y','d','u','i','n','o'}
872      #define MANUFACTURER_NAME_LEN	11
873      #define PRODUCT_NAME		{'N','K','R','O',' ','K','e','y','b','o','a','r','d'}
874     #define PRODUCT_NAME_LEN	13
875      #define EP0_SIZE		64
876      #define NUM_ENDPOINTS         5
877      #define NUM_USB_BUFFERS	14
878      #define NUM_INTERFACE		4
879      #define SEREMU_INTERFACE      1	// Serial emulation
880      #define SEREMU_TX_ENDPOINT    1
881      #define SEREMU_TX_SIZE        64
882      #define SEREMU_TX_INTERVAL    1
883      #define SEREMU_RX_ENDPOINT    2
884      #define SEREMU_RX_SIZE        32
885      #define SEREMU_RX_INTERVAL    2
886      #define KEYBOARD_INTERFACE    0	// Keyboard
887      #define KEYBOARD_ENDPOINT     3
888      #define KEYBOARD_SIZE         8
889      #define KEYBOARD_INTERVAL     1
890      #define KEYMEDIA_INTERFACE    2	// Keyboard Media Keys
891      #define KEYMEDIA_ENDPOINT     4
892      #define KEYMEDIA_SIZE         8
893      #define KEYMEDIA_INTERVAL     4
894      #define NKRO_INTERFACE        3	// NKRO Keyboard
895      #define NKRO_ENDPOINT         5
896      #define NKRO_SIZE             32
897      #define NKRO_REPORT_KEYS		( NKRO_SIZE - 1 )
898      #define NKRO_INTERVAL         1
899      #define ENDPOINT1_CONFIG	ENDPOINT_TRANSMIT_ONLY
900      #define ENDPOINT2_CONFIG	ENDPOINT_RECEIVE_ONLY
901      #define ENDPOINT3_CONFIG	ENDPOINT_TRANSMIT_ONLY
902      #define ENDPOINT4_CONFIG	ENDPOINT_TRANSMIT_ONLY
903      #define ENDPOINT5_CONFIG	ENDPOINT_TRANSMIT_ONLY
904      #define ENDPOINT6_CONFIG	ENDPOINT_TRANSMIT_ONLY
905
906    #elif defined(USB_SERIAL_NKRO)
907      #define VENDOR_ID		0x16C0
908      #define PRODUCT_ID		0x0487
909      #define DEVICE_CLASS		0xEF
910      #define DEVICE_SUBCLASS	0x02
911      #define DEVICE_PROTOCOL	0x01
912      #define MANUFACTURER_NAME	{'T','e','e','n','s','y','d','u','i','n','o'}
913      #define MANUFACTURER_NAME_LEN	11
914      #define PRODUCT_NAME		{'S','e','r','i','a','l','/','N','K','R','O',' ','K','e','y','b','o','a','r','d'}
915      #define PRODUCT_NAME_LEN	20
916      #define EP0_SIZE		64
917      #define NUM_ENDPOINTS         6
918      #define NUM_USB_BUFFERS	14
919      #define NUM_INTERFACE		5
920      #define CDC_IAD_DESCRIPTOR	1
921      #define CDC_STATUS_INTERFACE	0
922      #define CDC_DATA_INTERFACE	1	// Serial
923      #define CDC_ACM_ENDPOINT	2
924      #define CDC_RX_ENDPOINT       3
925      #define CDC_TX_ENDPOINT       4
926      #define CDC_ACM_SIZE          16
927      #define CDC_RX_SIZE           64
928      #define CDC_TX_SIZE           64
929      #define KEYBOARD_INTERFACE    2	// Keyboard
930      #define KEYBOARD_ENDPOINT     1
931      #define KEYBOARD_SIZE         8
932      #define KEYBOARD_INTERVAL     1
933      #define KEYMEDIA_INTERFACE    3	// Keyboard Media Keys
934      #define KEYMEDIA_ENDPOINT     5
935      #define KEYMEDIA_SIZE         8
936      #define KEYMEDIA_INTERVAL     4
937      #define NKRO_INTERFACE        4	// NKRO Keyboard
938      #define NKRO_ENDPOINT         6
939      #define NKRO_SIZE             32
940      #define NKRO_REPORT_KEYS		( NKRO_SIZE - 1 )
941      #define NKRO_INTERVAL         1
942      #define ENDPOINT1_CONFIG	ENDPOINT_TRANSMIT_ONLY
943      #define ENDPOINT2_CONFIG	ENDPOINT_TRANSMIT_ONLY
944      #define ENDPOINT3_CONFIG	ENDPOINT_RECEIVE_ONLY
945      #define ENDPOINT4_CONFIG	ENDPOINT_TRANSMIT_ONLY
946      #define ENDPOINT5_CONFIG	ENDPOINT_TRANSMIT_ONLY
947      #define ENDPOINT6_CONFIG	ENDPOINT_TRANSMIT_ONLY
948    #endif
949    
950    #ifdef USB_DESC_LIST_DEFINE
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_desc.c` add lines 239-265

```c
236    };
237    #endif
238    
239    #ifdef NKRO_INTERFACE
240    // Via https://dawnmist.dreamwidth.org/1250.html
241    static uint8_t nkro_hid_report_desc[] = {
242            0x05, 0x01, // Usage Page (Generic Desktop),
243            0x09, 0x06, // Usage (Keyboard),
244            0xA1, 0x01, // Collection (Application),
245            // bitmap of modifiers
246            0x75, 0x01, // Report Size (1),
247            0x95, 0x08, // Report Count (8),
248            0x05, 0x07, // Usage Page (Key Codes),
249            0x19, 0xE0, // Usage Minimum (224),
250            0x29, 0xE7, // Usage Maximum (231),
251            0x15, 0x00, // Logical Minimum (0),
252            0x25, 0x01, // Logical Maximum (1),
253            0x81, 0x02, // Input (Data, Variable, Absolute), ;Modifier byte
254            // bitmap of keys
255            0x95, NKRO_REPORT_KEYS*8, // Report Count (),
256            0x75, 0x01, // Report Size (1),
257            0x15, 0x00, // Logical Minimum (0),
258            0x25, 0x01, // Logical Maximum(1),
259            0x05, 0x07, // Usage Page (Key Codes),
260            0x19, 0x00, // Usage Minimum (0),
261            0x29, NKRO_REPORT_KEYS*8-1, // Usage Maximum (),
262            0x81, 0x02, // Input (Data, Variable, Absolute),
263            0xc0 // End Collection
264    };
265    #endif
266    
267    #ifdef JOYSTICK_INTERFACE
268    #if JOYSTICK_SIZE == 12
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_desc.c` add lines 603-610 and modify line 612

```c
600    #define MULTITOUCH_INTERFACE_DESC_SIZE	0
601    #endif
602    
603    // Via https://dawnmist.dreamwidth.org/1250.html
604    #define NKRO_INTERFACE_DESC_POS	MULTITOUCH_INTERFACE_DESC_POS+MULTITOUCH_INTERFACE_DESC_SIZE
605    #ifdef  NKRO_INTERFACE
606    #define NKRO_INTERFACE_DESC_SIZE	9+9+7
607    #define NKRO_HID_DESC_OFFSET	NKRO_INTERFACE_DESC_POS+9
608    #else
609    #define NKRO_INTERFACE_DESC_SIZE	0
610    #endif
611    
612    #define CONFIG_DESC_SIZE		NKRO_INTERFACE_DESC_POS+NKRO_INTERFACE_DESC_SIZE
613    
614    
615    
616    // **************************************************************
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_desc.c` add lines 1131-1158

```c
1129   #endif // JOYSTICK_INTERFACE
1130   
1131   #ifdef NKRO_INTERFACE
1132           // interface descriptor, USB spec 9.6.5, page 267-269, Table 9-12
1133           9,                                      // bLength
1134           4,                                      // bDescriptorType
1135           NKRO_INTERFACE,                         // bInterfaceNumber
1136           0,                                      // bAlternateSetting
1137           1,                                      // bNumEndpoints
1138           0x03,                                   // bInterfaceClass (0x03 = HID)
1139           0x00,                                   // bInterfaceSubClass (0x01 = Boot)
1140           0x00,                                   // bInterfaceProtocol (0x01 = Keyboard)
1141           0,                                      // iInterface
1142           // HID interface descriptor, HID 1.11 spec, section 6.2.1
1143           9,                                      // bLength
1144           0x21,                                   // bDescriptorType
1145           0x11, 0x01,                             // bcdHID
1146           0,                                      // bCountryCode
1147           1,                                      // bNumDescriptors
1148           0x22,                                   // bDescriptorType
1149           LSB(sizeof(nkro_hid_report_desc)),      // wDescriptorLength
1150           MSB(sizeof(nkro_hid_report_desc)),
1151           // endpoint descriptor, USB spec 9.6.6, page 269-271, Table 9-13
1152           7,                                      // bLength
1153           5,                                      // bDescriptorType
1154           NKRO_ENDPOINT | 0x80,                   // bEndpointAddress
1155           0x03,                                   // bmAttributes (0x03=intr)
1156           NKRO_SIZE, 0,                           // wMaxPacketSize
1157           NKRO_INTERVAL,                          // bInterval
1158   #endif // NKRO_INTERFACE
1159   
1160   #ifdef MTP_INTERFACE
```

In `arduino\hardware\teensy\avr\cores\teensy3\usb_desc.c` add lines 1602-1605

```c
1600           {0x2100, MULTITOUCH_INTERFACE, config_descriptor+MULTITOUCH_HID_DESC_OFFSET, 9},
1601   #endif
1602   #ifdef NKRO_INTERFACE
1603           {0x2200, NKRO_INTERFACE, nkro_hid_report_desc, sizeof(nkro_hid_report_desc)},
1604           {0x2100, NKRO_INTERFACE, config_descriptor+NKRO_HID_DESC_OFFSET, 9},
1605   #endif
1606   #ifdef MTP_INTERFACE
```

In `arduino\hardware\teensy\avr\boards.txt` add lines 1175-1177
```
1174    teensyLC.menu.usb.flightsim.fake_serial=teensy_gateway
1175    teensyLC.menu.usb.nkrokeyboard=NKRO Keyboard
1176    teensyLC.menu.usb.nkrokeyboard.build.usbtype=USB_NKRO
1177    teensyLC.menu.usb.nkrokeyboard.fake_serial=teensy_gateway
1178    teensyLC.menu.usb.disable=No USB
```

## Configuring the Firmware and IDE

There are a number of options built into the firmware to give you flexibility in your implementation. These are presented as preprocessor defines that can be commented and uncommented to fit.

All user-editable defines are in `Config.h`, see the comments for additional information.

If you are not using either the Pro Micro or Teensy LC boards provided in this repo, it may be necessary to change the definitions of the pins, located in `PinConfig.h`.

If you do not have the FastLED and HID-Project libraries installed, do so though the `Tools->Manage Libraries` menu.

#### Compiling

When using a Pro Micro, select `Arduino/Genuino Micro` from `Tools->Board`.

When using a Teensy LC, select `Teensy LC` from `Tools->Board`, then select `NKRO Keyboard` from `Tools->USB Type` for reactive lights. If you are using serial light updates, select `Serial + NKRO Keyboard`.

Prior to compilation, review the (numerous) options available to the end user in `Config.h`. Comment and uncomment the corresponding options that match your setup.

## Running the Software

#### Configuring

To be revised.

#### Power On

To be revised.

#### Output

By default, the program will run in NKRO Keyboard mode. The specific keyboard keys are set in `USBOutput.cpp`, but are listed here in order of left to right:
```
a z s x d c f v g b h n j m k ,
```
When a second finger touches the pad, the following keys are pressed in order of left to right
```
1 q 2 w 3 e 4 r 5 t 6 y 7 u 8 i
```

By default, the air sensor functions as follows:
- `Home` is held as long as any sensor is triggered and released when there are no sensors triggered.
- `End` is pressed when any motion is detected, as long as the hand was previously in front of the sensors.
- `Page Up` is pressed and released when the sensor detections movement upwards.
- `Page Down` is pressed and released when the sensor detections movement downwards.

If `#define IR_SENSOR_KEY` is uncommented, each air sensor will report back individually. The default binding from bottom to top is:
```
/ . ' ; ] [
```
Per US QWERTY layout.