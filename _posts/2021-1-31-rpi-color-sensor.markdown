---
layout: post
title: Color Sensor အား Raspberry Pi ဖြင့် အသုံးပြုခြင်း
date: 2021-1-31 13:32:20 +0630
description: Color sensing with Raspberry Pi
img: TCS3200/color-rpi.jpg
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Sensor]
---
Raspberry Pi မှာ Red, Green, Blue (RGB) စတဲ့ အရောင်တွေ ခွဲခြားပြီး color detect ပြုလုပ်နိုင်ဖို့ TCS3200 ဆိုတဲ့ color sensor ကို RobotDyn နဲ့ Waveshare က ထုတ်တဲ့ အမျိုးအစား ၂မျိုးရှိပြီး နှစ်သက်ရာ ရွေးချယ်အသုံးပြု နိုင်ပါတယ်။ TCS3200 အပြင် ဈေးနှုန်းသင့်တဲ့ TCS230 color sensor ကိုလည်း သုံးနိုင်ပါတယ်။ ဒီအမျိုးအစား ၂ခုလုံးမှာ built-in white LED light ၄လုံးစီ ပါရှိပြီးတော့ color sensor ဟာ RGB အရောင်တွေအပေါ်မှာ အလင်းပြန်မှုပေါ် မူတည်ပြီး color detect ပြုလုပ်ခြင်း ဖြစ်တဲ့အတွက် ပတ်ဝန်းကျင်ရဲ့ အလင်းရောင် ပြောင်းလဲမှုပေါ်မူတည်ပြီး calibrate လုပ်ထားတဲ့ RGB တန်ဖိုးတွေ အပြောင်းအလဲ ဖြစ်နိုင်တယ်ဆိုတာကို သတိထားရပါမယ်။

Color Sensor ရဲ့ အလယ်မှာ 8x8 Matrix ပုံစံ စီထားတဲ့ Photodiode လေးတွေ ၆၄လုံး ပါရှိပြီးတော့ ဒီ Photodiode တွေကနေ ဖတ်လို့ရရှိလာတဲ့ Light intensity တန်ဖိုးတွေကို Current to Frequency Converter တစ်ခု အသုံးပြုပြီး frequency square wave form တစ်ခုအဖြစ် ပြောင်းလဲကာ ထုတ်ပေးပါတယ်။ ဒီ square wave output တွေဖြစ်တဲ့ raw data တန်ဖိုးတွေကို Raspberry Pi ကနေ ဖတ်ပြီး အရောင်တွေအဖြစ် ပြန်လည်စီစဉ် ဖော်ပြပေးရမှာ ဖြစ်ပါတယ်။

Sersor ရဲ့ အလယ်က 8x8 Matrix ပုံသဏ္ဍာန် Photodiode ၆၄လုံးကို အနီးကပ် ကြည့်ရှုမယ်ဆိုရင် Red, Green, Blue အရောင်တွေအတွက် မတူညီတဲ့ color filter အပိုင်း ၃ပိုင်းကို တွေ့ရမှာဖြစ်ပါတယ်။ RGB ၃ရောင်အတွက် Photodiode ၁၆လုံးစီ filter အဖြစ် တပ်ဆင်ထားတာ ဖြစ်ပြီးတော့ ကျန်တဲ့ ၁၆လုံးကတော့ color filter မဟုတ်တဲ့ clear photodiode တွေ ဖြစ်ပါတယ်။

Sensor ရဲ့ pin တွေကို ကြည့်မယ်ဆိုရင် S0, S1, S2, S3 ဆိုတဲ့ ၄ပင်ကို တွေ့ရမှာပါ။ S0 နဲ့ S1 က Sensor ကနေ ထွက်လာမယ့် output frequency တန်ဖိုးတွေကို သတ်မှတ်ပေးတဲ့ ပင်တွေဖြစ်ပြီး ဒီ၂ပင်ကို Gnd မှာ ချိတ်ဆက် လိုက်မယ်ဆိုရင် Power Down သွားမှာ ဖြစ်ပြီးတော့၊ ၂ပင်လုံးကို 5V မှာ ချိတ်ဆက်ပေးလိုက်ရင် output frequency 100% (500 - 600 KHz) ထွက်ရှိမှာ ဖြစ်ပါတယ်။ တကယ်လို့ S0 ကို Gnd ၊ S1 ကို 5V ပေးရင် output frequency 2% (10 - 12 KHz) ထွက်ရှိမှာဖြစ်ပြီး S0 ကို 5V ၊ S1 ကို Gnd ပေးရင် 20% (100 - 120 KHz) ထွက်ရှိမှာ ဖြစ်ပါတယ်။ ယခုစမ်းသပ်ခြင်းမှာတော့ 100% frequency ရရှိအောင် ၂ပင်လုံးကို 5V မှာပဲ ချိတ်ဆက်ပေးပါမယ်။

S2 နဲ့ S3 ပင်တွေကိုတော့ Photodiode Selection pin တွေလို့ ခေါ်ဆိုပြီး ဒီ ၂ပင် ကို GPIO pin တွေကနေ High သို့မဟုတ် Low signal တွေ ပေးပို့ကာ Photodiode ကနေ ပေးပို့တဲ့ light intensity ကို သက်ဆိုင်ရာ အရောင်တွေအဖြစ် ခွဲခြားပေးပါတယ်။ ဥပမာ - S2 နဲ့ S3 ၂ပင်လုံးကို Low Signal ပေးပို့ထားရင် ဖတ်လို့ရရှိလာတဲ့ raw data တန်ဖိုးတွေက အနီရောင်ကို ရည်ညွှန်းတဲ့ တန်ဖိုးတွေ ဖြစ်လာပါလိမ့်မယ်။ အောက်ပါ ဇယားကို ကြည့်ပြီး RGB ၃ရောင်အတွက် S2 နဲ့ S3 ၂ပင်ကို GPIO တွေကနေ signal ရွေးချယ် ပေးပို့ကာ အရောင်ခွဲနိုင်ပါတယ်။

S2 | S3 | Color Select
Low | Low | Red
Low | High | Blue
High | Low | Clear
High | High | Green

OE pin ကတော့ 74HC595 နဲ့ PCA9685 မှာ ပါဝင်တဲ့ OE pin တွေကဲ့သို့ Output Enable Pin ဖြစ်ပြီး Low Level Active pin ဖြစ်လို့ Gnd မှာပဲ ချိတ်ဆက်ပေးရပါမယ်။ OUT လို့ ရေးထားတဲ့ Output pin က 50% duty cycle ရှိတဲ့ square wave ကို High to Low (falling edge) ဖြစ်သွားမယ့် အချိန်မှာ ထုတ်ပေးမယ့် signal pin ဖြစ်ပါတယ်။

<p align="center">
<img src="/assets/img/TCS3200/tcs3200.jpeg">
<br>
<a>ပုံ ၊ Waveshare TCS3200 Color Sensor</a>
</p>

TCS3200 Sensor နဲ့ Raspberry Pi ကို အောက်ပါအတိုင်း ချိတ်ဆက်နိုင်ပြီး Waveshare က ထုတ်တဲ့ TCS3200 အမျိုးအစားမှာတော့ built-in LED ကို 5V မှာ တပ်ဆင်ပြီး အဖွင့်အပိတ် လုပ်နိုင်အောင် LED ဆိုတဲ့ pin တစ်ပင် ပေးထားပါ တယ်။ အသုံးမပြုလိုရင် အလွတ်ထားနိုင်ပါတယ်။


TCS3200 Color Sensor Pin | Raspberry Pi Pin
Gnd | Gnd
OE | Gnd
Vcc | 5V
S0 | 5V
S1 | 5V
S2 | BCM GPIO 23
S3 | BCM GPIO 24
OUT | BCMGPIO 25

<p align="center">
<img src="/assets/img/TCS3200/color-wiring.png">
<br>
<a>ပုံ ၊ Raspberry Pi နှင့် color sensor ချိတ်ဆက်ခြင်း</a>
</p>

ချိတ်ဆက်ပြီးတဲ့နောက် color raw data တန်ဖိုးတွေကို အရင်ဆုံးဖတ်ပြီး RGB တန်ဖိုးတွေ calibrate လုပ်ဖို့ အောက်ပါ program ကို တည်ဆောက်လိုက်ပါ။aaaaaa

`$ sudo nano raw_rgb.py`

<pre><code class="language-python line-numbers">
import RPi.GPIO as GPIO
import time
s2 = 23
s3 = 24
signal = 25
NUM_CYCLES = 10
def setup():
  GPIO.setmode(GPIO.BCM)
  GPIO.setup(signal,GPIO.IN, pull_up_down=GPIO.PUD_UP)
  GPIO.setup(s2,GPIO.OUT)
  GPIO.setup(s3,GPIO.OUT)
  print("\n")
def loop():
  temp = 1
  while(1):
    GPIO.output(s2,GPIO.LOW)
    GPIO.output(s3,GPIO.LOW)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    red  = NUM_CYCLES / duration
    print("red value - ",red)
    GPIO.output(s2,GPIO.LOW)
    GPIO.output(s3,GPIO.HIGH)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    blue = NUM_CYCLES / duration
    print("blue value - ",blue)
    GPIO.output(s2,GPIO.HIGH)
    GPIO.output(s3,GPIO.HIGH)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    green = NUM_CYCLES / duration
    print("green value - ",green)
    time.sleep(2)
def endprogram():
    GPIO.cleanup()
if __name__=='__main__':
    setup()
    try:
        loop()
    except KeyboardInterrupt:
        endprogram()
</code></pre>

`$ sudo python raw_rgb.py`

<p align="center">
<img src="/assets/img/TCS3200/raw-data.png">
<br>
<a>ပုံ ၊ Raw data တန်ဖိုးများ ဖတ်ခြင်း</a>
</p>

raw_rgb.py ကို run ပြီး အနီရောင် စာရွက်ဖြစ်စေ၊ အပြာရောင် အစိမ်းရောင် စာရွက်ဖြစ်စေ Sensor ရဲ့ Photodiode ရှေ့ကို ကပ်ကြည့်ပြီး Terminal မှာ print ပြနေတဲ့ Red, Green, Blue တန်ဖိုးတွေကို မှတ်သားထားရပါမယ်။ နမူနာ အနေနဲ့ အနီရောင် စာရွက်ကပ်ပြီး ဖတ်ကြည့်လိုက်တဲ့အခါ green က ပျမ်းမျှ တန်ဖိုး 7000 အောက်၊ blue က 9000 အောက်၊ red က 11000 အထက် ဆိုပြီး ပျမ်းမျှတန်ဖိုးတွေ ရလာပါမယ်။ ဒီတန်ဖိုးတွေပေါ်မူတည်ပြီး အရောင် တစ်ခုခု ကပ်ကြည့်တဲ့အခါ red, green, blue ဆိုပြီး Terminal မှာ print ပြတဲ့ အပိုင်းကို program ရဲ့ အောက်နားမှာ ထပ်ဖြည့် ရေးသားနိုင်ပါတယ်။ ဒီလို ရေးသားထားတဲ့ Program အပြည့်အစုံကတော့ အောက်ပါအတိုင်းပဲ ဖြစ်ပါတယ်။

`$ sudo nano color_detector.py`

<pre><code class="language-python line-numbers">
import RPi.GPIO as GPIO
import time
s2 = 23
s3 = 24
signal = 25
NUM_CYCLES = 10
def setup():
  GPIO.setmode(GPIO.BCM)
  GPIO.setup(signal,GPIO.IN, pull_up_down=GPIO.PUD_UP)
  GPIO.setup(s2,GPIO.OUT)
  GPIO.setup(s3,GPIO.OUT)
  print("\n")
def loop():
  temp = 1
  while(1):
    GPIO.output(s2,GPIO.LOW)
    GPIO.output(s3,GPIO.LOW)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    red  = NUM_CYCLES / duration
    GPIO.output(s2,GPIO.LOW)
    GPIO.output(s3,GPIO.HIGH)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    blue = NUM_CYCLES / duration
    GPIO.output(s2,GPIO.HIGH)
    GPIO.output(s3,GPIO.HIGH)
    time.sleep(0.3)
    start = time.time()
    for impulse_count in range(NUM_CYCLES):
      GPIO.wait_for_edge(signal, GPIO.FALLING)
    duration = time.time() - start
    green = NUM_CYCLES / duration
    if green<7000 and blue<9000 and red>11000:
      print("red")
      temp=1
    elif red<14000 and  blue>13000 and green<14000:
      print("green")
      temp=1
    elif green>15000 and red<11500 and blue>23000:
      print("blue")
      temp=1
    elif red<10000 and green<9000 and \
    blue<10000 and temp==1:
      print("place the object.....")
      temp=0
def endprogram():
    GPIO.cleanup()
if __name__=='__main__':
    setup()
    try:
        loop()
    except KeyboardInterrupt:
       endprogram()
</code></pre>

`$ sudo python color_detector.py`

အထက်ပါအတိုင်း run ကြည့်လိုက်တဲ့အခါ Sensor ရှေ့မှာ Red, Green, Blue အရောင်တွေ မပြလို့ raw data တန်ဖိုးတွေထဲမှာ တစ်ခုမှ အကျုံးမဝင်ရင် place the object လို့ ပြနေမှာ ဖြစ်ပြီး အရောင်တစ်ခုခု ကပ်ပြလိုက်တဲ့အခါမှ color အမည်ကို print ပြသမှာ ဖြစ်ပါတယ်။

<p align="center">
<img src="/assets/img/TCS3200/color-detect.png">
<br>
<a>ပုံ ၊ Color detect ပြုလုပ်ခြင်း</a>
</p>

အထက်ပါ Program များကို <a style="text-decoration:none" href="https://github.com/kogyikaunghtet/allaboutRpi/tree/master/Sensors/Color%20Sensor">ဒီနေရာ</a> မှာလည်း ရယူနိုင်ပါတယ်။ ဝါ၊ စိမ်း၊ နီ LED မီးများ တပ်ဆင်ပြီးတော့လည်း စက္ကူရောင်စုံများ ကပ်ကြည့်ရင် သက်ဆိုင်ရာ LED မီး လင်းစေတဲ့ Program များလည်း စမ်းသပ်ကြည့်ကြပါ။

<p align="center">
<img src="/assets/img/TCS3200/red.jpg">
<br>
<a>ပုံ ၊ စက္ကူအနီရောင် ပြသပြီး LED အနီ လင်းစေခြင်း</a>
</p>

<p align="center">
<img src="/assets/img/TCS3200/yellow.jpg">
<br>
<a>ပုံ ၊ စက္ကူအဝါရောင် ပြသပြီး LED အဝါ လင်းစေခြင်း</a>
</p>

<p align="center">
<img src="/assets/img/TCS3200/green.jpg">
<br>
<a>ပုံ ၊ စက္ကူအစိမ်းရောင် ပြသပြီး LED အစိမ်း လင်းစေခြင်း</a>
</p>


