# Ambilight-TV
General guide to how to make Ambilight to your non-phillips TV with pictures and demonstration, using [raspberry pi](https://www.raspberrypi.com/products/raspberry-pi-zero/) and [hyperion](https://docs.hyperion-project.org/en/user/Installation.html) software. (Known also as back-light TV).

## Table Of Contents
- [Ambilight-TV](#ambilight-tv)
  * [Intro](#intro)
      - [Important Notes:](#important-notes-)
  * [Table Of Contents](#table-of-contents)
  * [Requirments](#requirments)
    + [To Order List (If you don't have already by chance)](#to-order-list--if-you-don-t-have-already-by-chance-)
    + [Optional List](#optional-list)
    + [Special Considerations](#special-considerations)
  * [Setup](#setup)
      - [Overview](#overview)
  * [Demo](#demo)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>



## Intro
Hue Ambilight is known feature in [phillips' TV](https://www.youtube.com/watch?v=aH-4HxWgk1k). The TV equipped with back RGB leds behind the TV, they dynamically change the colour by the current value of the edge pixels of the TV's image. It began when I was impressed in personal from ambilight in my friend TV house. 
ecause this kind of TVs are usually more expensive, I decided to build my own ambilight to my non-phillips TV setup and share the result with some tips and info about the process.
Enjoy. 
Credits 
- ["The ULTIMATE Guide to Building an Ambilight TV with Hyperion"](https://www.youtube.com/watch?v=J26oYlKyq7Q) by ["Everything Smart Home"](https://www.youtube.com/c/EverythingSmartHome) 
- [Hyperion](https://docs.hyperion-project.org/en/user/Installation.html) Software to run on the raspberry pi which control the lights.
#### Important Notes
 -  This will work only if your source is external to the TV (like Xioami Streamer, Xbox Console or Blueray player), won't work for Smart-TV internal applications. In other words, if you play Netflix through your Xbox, it is OK, but if you play it from your Smart-TV's internal device, you won't see the ambilight effect
 -  The discussed setup was verified on 55" TV, if your TV is larger than 55" then you may need to modify the setup (please check [Special Considerations](#special-considerations)


## Requirments
A short list of everything you will need for the BackLight leds TV project
Links are suitable for shipping to Israel. Once you have all you good to go.
- A Television (Obviously) 
### To Order List (If you don't have already by chance)
- [ ] [4K Video Capture](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911092523&origin=y&SearchText=4K+USB+3.0+Video+Capture+Card+HDMI-compatible&spm=a2g0o.detail.1000002.0) - see [example](Images/RecordingCard.png)
- [ ] [Power Supply](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911093849&SearchText=DC+5V+12V+24V+lighting+transformer+AC+110V+220V+sw&spm=a2g0o.productlist.1000002.0) 5V, 5A and EU plug should be suffiecnt for 5m strip - see [example](Images/PowerSupply.png)
- [ ] [DC Power female connector](https://www.aliexpress.com/wholesale?SearchText=5%205mm%20x%202.5mm%20dc%20power%20plug%20female)You need only one piece - see [example](Images/Power-Connector.png)
- [ ] [LED Strip](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911101259&origin=y&SearchText=DC5V+WS2812B&spm=a2g0o.detail.1000002.0) - WS2812B ,Black/White PCB, 60 IP30, 5m is enough for 55” TV,if you have bigger TV size then check [Special Considerations](#special-considerations). You should measure your TV’s width and height if you are unsure. - see [example](Images/Leds.png)
- [ ] Any kind of [Raspberry Pi](https://piitel.co.il/cats/v1-3-p-zero/?src=raspberrypi) - even an old one is ok (I used Raspberry Pi 2)
    - [ ] In addition you will need [micro SD card](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911102936&origin=y&SearchText=4GB+micro+sd+card&spm=a2g0o.detail.1000002.0) of at least 4 GB

### Optional List
- [ ] [HDMI Switcher](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911093559&SearchText=hdmi+switcher+3+to+1+remote&spm=a2g0o.productlist.1000002.0) in case you have several devices to connected to  your TV (AppleTV and Xbox for example).
- [ ] **Simple Wire Stripper** - [buy](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911155257&SearchText=Durable+Wire+Stripper+Decrustation+Pliers+&spm=a2g0o.order_list.1000002.0) or borrow from one of your electricians friends, needed to connect the raspberry pi to the power supply.
- [ ] **Micro USB Cable** - [buy]( https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20220911155346&SearchText=micro+usb+cable&spm=a2g0o.productlist.1000002.0) or use an old you already have if you don't mind to cut it
- [ ] **double side glue tape** - for sticking the raspberry pi and the capture box on the back of your TV. ([link](https://www.aliexpress.com/wholesale?catId=0&initiative_id=AS_20220911160510&origin=y&SearchText=2+sides+tape&spm=a2g0o.detail.1000002.0))


### Special Considerations
If your TV's size is bigger then 55" you may need to revise the next settings:
- **Leds Strip's Lenght:** You should measure the actual length of your height and width of your TV to check if you may need more then 5m strip.
- **Choosing the right Power Supply:** If you need more then 5m of led strip, you may need a bigger power supply. [This video](https://www.youtube.com/watch?v=1UprhxCzVuI) explains in brief how to calculate the needed watts for the Leds.


## Setup
After preparing all important stuff you are ready to go, follow the instructions of the video. 
Sometimes the setup can be confusing a little, but worry not. I added a few diagrams to make for clearfication. 
#### Overview 
The next graph demonstrate the connection of all compenents in the setup 
```mermaid
graph TD;
    A[External Source]-->|HDMI| B[Capture Card];
    B-->|HDMI| TV;
    B-->|USB-USB Cable| C[Raspberry Pi];
    C-->|Connector| D{Leds};
```
The power of the rpi and leds
```mermaid
graph TD;
    A(Power Supply)-->B[DC power Connector];
    B-->|microUSB stripped cable| C[Raspberry Pi];
    B-->|red-black cables| D{Leds};
```
## Demo
