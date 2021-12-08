---
layout: post
title: Ultrasonic Sensor အား Raspberry Pi ဖြင့် အသုံးပြုခြင်း
date: 2020-02-13 13:32:20 +0630
description: Ultrasonic Sensor အား Raspberry Pi ဖြင့် အသုံးပြုခြင်း
img: ultrasonic/hc-sr04.jpg
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Sensor]
---
HC-SR04 Ultrasonic Sensor က distance တိုင်းတာတဲ့နေရာတွေမှာ အသုံးပြုနိုင်ပြီး 2cm ကနေ 450cm အထိ တိုင်းတာနိုင်တဲ့အပြင် accuracy ကလည်း 3mm ခန့်သာ ဖြစ်လို့ အတော်တိကျကောင်းမွန်စွာ တိုင်းတာနိုင်ပါတယ်။ လူတွေ သာမာန်အားဖြင့် ကြားနိုင်တဲ့ အသံတွေက 20 to 20,000 Hz ကြားထဲမှာ ရှိပြီး 20Hz ထက် နည်းရင် infrasound ၊ 20,000Hz ထက် များရင် ultrasound လို့ ခေါ်ပါတယ်။ ultrasonic sensor က သူ့ရဲ့ transmitter မျက်လုံးလေး ဘက်ကနေ Ultrasound wave တစ်ခုကို ထုတ်လွှင့်ကာ obstacle သို့မဟုတ် solid object တစ်ခုခုကို ရိုက်ခတ်ပြီး ပြန်လာတဲ့ echo ပဲ့တင်သံကို receiver ဘက်ကနေ ပြန်ဖမ်းယူပါတယ်။ ဒီလို obstacle ကို သွားရိုက်ခတ်ပြီး ပြန်လာတဲ့ ကြာချိန် Pulse duration နဲ့ Ultrasound wave ရဲ့ Speed တို့ကို မြှောက်ခြင်း အားဖြင့် လိုချင်တဲ့ Distance တန်ဖိုးကို တွက်ထုတ်ယူရခြင်းပဲ ဖြစ်ပါတယ်။

Ultrasonic Sensor ရဲ့ pin တွေကို ကြည့်ရင် Vcc, Trig, Echo, Gnd ဆိုပြီး ပင်၄ပင် တွေ့ရမှာဖြစ်ပါတယ်။ Trig (Trigger) က Ultrasound Wave တစ်ခု ထုတ်လွှင့်ပေးဖို့ pin ဖြစ်ပြီး ဒီ pin ကို အချိန်ကာလ တစ်ခုကြာအောင် High ပေးခြင်းအားဖြင့် ultrasound wave ကို ထုတ်လွှင့်နိုင်ပါတယ်။ Echo pin ကတော့ ပုံမှန် အခြေအနေမှာ LOW (0V) ရှိနေရမှာ ဖြစ်ပြီး sensor ရဲ့ transmitter ကနေ sound pulse တစ်ခုကို ထုတ်လွှင့်ပြီးနောက် echo pulse ပြန်ဝင်လာတဲ့ အချိန်မှာ High ဖြစ်သွားမှာ ဖြစ်ပါတယ်။ Low ဖြစ်နေတဲ့ အချိန်တန်ဖိုးထဲကနေ High ဖြစ်သွားတဲ့ အချိန်တန်ဖိုးကို နှုတ်ပေးခြင်းအားဖြင့် ပဲ့တင်သံ pulse ပြန်လာတဲ့ ကြာချိန် duration ကို တွက်ထုတ်ရမှာ ဖြစ်ပါတယ်။

Distance တွက်ထုတ်ဖို့ လိုအပ်တဲ့ pulse duration ကို သိရပြီဆိုရင် Speed of Sound တန်ဖိုးကိုတော့ ပျမ်းမျှ 343 m/s ကို ယူသုံးနိုင်ပါတယ်။ ဒီတန်ဖိုးက ပျမ်းမျှတန်ဖိုးသာ ဖြစ်ပြီး အပူချိန် 20°C ရှိတဲ့ ခြောက်သွေ့တဲ့ လေထုထဲက Speed of sound တန်ဖိုးသာ ဖြစ်ပါတယ်။ လေထုအပူချိန် အပြောင်းအလဲ၊ လေထုစိုထိုင်းဆ အတိုးအလျော့တွေပေါ်မူတည်ပြီး Speed of sound တန်ဖိုး ပြောင်းလဲနိုင်ပေမယ့် အနီးစပ်ဆုံးတန်ဖိုးဖြစ်တဲ့ 343 m/s ကိုပဲအသုံးပြုကြပါမယ်။ Unit ကိုတော့ cm (centimeter) နဲ့ပဲ ထွက်စေလိုတဲ့အတွက် ဒဿမတန်ဖိုး ၂လုံး ရွှေ့ရမှာ ဖြစ်လို့ 34300 cm/s ဖြစ်သွားပါမယ်။ ဒါပေမယ့် Echo pin ကနေ တွက်ထုတ်ပေးတဲ့ Pulse Duration ဟာ Transmitter ကနေ ultrasound wave ထွက်သွားပြီးနောက် obstacle ကို ရိုက်ခတ်ပြီး ပြန်လာတဲ့ အချိန်ကို ပေးနေတာ ဖြစ်လို့ Duration တန်ဖိုးက အသွား၁ဆ၊ အပြန်၁ဆ ဖြစ်နေပါတယ်။ ဒါကြောင့် Pulse Duration တန်ဖိုးကို ၂နဲ့ စားပေးရမှာ ဖြစ်ပြီး အောက်မှာ ပြသထားတဲ့ ညီမျှခြင်းအတိုင်း တွက်လိုက်ရင် Speed of Sound တန်ဖိုးက 17150 cm/s ကိုသာ ထည့်သုံးရတော့မှာ ဖြစ်ပါတယ်။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;34300=\frac{Distance}{Pulse Duration/2}" title="equation" /></center>
<br>
<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;17150=\frac{Distance}{Pulse Duration}" title="equation" /></center>

Transmitter pin ဖြစ်တဲ့ Trig pin ကနေ Ultrasound Wave တစ်ခု ထုတ်လွှင့်ဖို့ အတွက်ကတော့ 0.1MHz တန်ဖိုးရှိတဲ့ Frequency Pulse တစ်ခု ထုတ်လွှတ် ပေးရင် လုံလောက်ပါတယ်။ Frequency ပုံသေနည်းအရ F=1/T ဖြစ်လို့ 10µs (0.00001 second) ခန့် High ပေးလိုက်ရင် 0.1MHz Frequency ထွက်ပါပြီ။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;Frequency=\frac{1}{0.00001 second}=0.1MHz" title="equation" /></center>

Ultrasonic Sensor ကို Power Supply ပေးတဲ့အခါ သူ့ရဲ့ working voltage က 5V အပြည့်အဝ ရမှ အလုပ်လုပ်ဆောင်နိုင်တာဖြစ်လို့ Vcc ကို Raspberry Pi ရဲ့ 5V သို့ ချိတ်ဆက်ပေးရပါမယ်။ သို့ပေမယ့် Raspberry Pi ရဲ့ GPIO pin တွေက logic voltage 3.3V သာလျှင်ရှိတာကြောင့် သတိပြုရမယ့်အချက်တွေ ရှိပါတယ်။ Echo pin က sensor ကနေ output ထွက်မယ့် pin ဖြစ်ပြီး Raspberry Pi ဆီသို့ input signal အနေနဲ့ ဝင်မှာဖြစ်လို့ 5V signal pulse တွေ ဝင်ခိုင်းလို့ မရပါဘူး။ ဒါကြောင့် Raspberry Pi ရဲ့ GPIO pin ဆီကို ချိတ်ဆက်တဲ့အခါ All About Raspberry Pi စာအုပ်ရဲ့ အခန်း(၅)မှာ ဖော်ပြခဲ့သလိုမျိုး resistor ၂လုံး သုံးပြီး Potential divider တည်ဆောက်ကာ ချိတ်ဆက်ပေးရပါမယ်။ R1 တန်ဖိုးကို 1.5KΩ အသုံးပြုပြီး၊ R2 တန်ဖိုးကို 680Ω အသုံးပြုပါက 3.44V ဝန်းကျင်ရမှာ ဖြစ်လို့ Echo pin ကို Raspberry Pi ရဲ့ GPIO မှာ ချိတ်ဆက်ဖို့ အဆင်ပြေသွားပါလိမ့်မယ်။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;Vo ut=V in\frac{R2}{R1 + R2}" title="equation" /></center>
<br>
<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;V out=5V \frac{1.5K\Omega }{680\Omega  + 1.5K\Omega }=3.44V" title="equation" /></center>

<p align="center">
<img src="/assets/img/ultrasonic/ult_rpi.jpg">
<br>
<a>ပုံ၊ Raspberry Pi နှင့် Ultrasonic Sensor ချိတ်ဆက်ခြင်း</a>
</p>

အထက်ပါ ပုံအတိုင်း Ultrasonic Sensor နဲ့ Raspberry Pi ကို ချိတ်ဆက်ပြီး အောက်ပါ Python Program နဲ့ စမ်းသပ်ကြည့်ပါ။

`$ sudo nano ultrasonic.py`

{% highlight python %}
import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BCM)
trig = 23
echo = 24
GPIO.setup(trig,GPIO.OUT)
GPIO.setup(echo,GPIO.IN)
GPIO.output(trig,GPIO.LOW)
try:
    while 1:
       GPIO.output(trig,GPIO.HIGH)
       time.sleep(0.00001)
       GPIO.output(trig,GPIO.LOW)

       while GPIO.input(echo)==0:
          pulse_start = time.time()
       while GPIO.input(echo)==1:
          pulse_end = time.time()

       pulse_duration = pulse_end - pulse_start
       distance = pulse_duration * 17150
       distance = round(distance, 2)
       print "Distance:",distance,"cm"
       time.sleep(0.5)
except KeyboardInterrupt:
     GPIO.cleanup()
{% endhighlight %}

`$ sudo python ultrasonic.py`

Program ကို run ကြည့်လိုက်ရင် အောက်ဖော်ပြပါ ပုံအတိုင်း Distance တန်ဖိုးတွေကို တွေ့မြင်ရပါမယ်။ Program ထဲမှာ ပထမဦးစွာ Trigger Pin ကို Frequency မထွက်အောင် Low signal ပေးထားပြီးမှ 10µs (0.00001 second) ကြာအောင် High ပေးပါတယ်။ High နဲ့ Low ကို တစ်လှည့်စီ ထုတ်ပေးခြင်းအားဖြင့် နေရာ အပြောင်းအလဲ ရွေ့နေတဲ့ Solid Object တွေဆီကို Frequency အသစ်တွေ သွားရိုက်ခတ်ပြီး Duration အသစ်နဲ့ Distance တန်ဖိုးအသစ်တွေ ထုတ်ပေး စေမှာ ဖြစ်ပါတယ်။ pulse duration ရဖို့အတွက်တော့ Unit က second နဲ့ floating point တန်ဖိုးတွေ ပေးတဲ့ time method သုံးပြီး ထုတ်လိုက်ပါတယ်။ Echo pin ဆီကို pulse ပြန်ဝင်လာလို့ 1 (High) ဖြစ်သွားတဲ့အချိန် ရောက်မှ duration end ဖြစ်ပြီး start duration ထဲက နှုတ်လိုက်ပါတယ်။
Distance တန်ဖိုးတွေကို ဒဿမနောက်မှာ ၂လုံးသာ ဖော်ပြစေ လိုတာ ဖြစ်လို့ Python ရဲ့ built-in function တစ်ခုဖြစ်တဲ့ round() နဲ့ floating point number ၂ခုသာ သတ်မှတ်ထားပါတယ်။

<p align="center">
<img src="/assets/img/ultrasonic/ss.png">
<br>
<a>ပုံ၊ Ultrasonic Sensor မှ Distance တန်ဖိုး ဖတ်ခြင်း</a>
</p>

ဆက်လက်ပြီး LED အနီရောင်တစ်လုံးနဲ့ အစိမ်းရောင်တစ်လုံးကို GPIO 17 နဲ့ 27 မှာ တပ်ဆင်ပြီး distance တန်ဖိုး 10cm အောက်ကို ရောက်ရင် အနီလင်း၊ အစိမ်း ပိတ်ကာ 10cm အထက်ဖြစ်သွားပါက အနီပိတ်၊ အစိမ်းလင်းစေတဲ့ project လေးကို ပြုလုပ်ကြည့်နိုင်ပါတယ်။

`$ sudo nano ultrasonicLED.py`

{% highlight python %}
import RPi.GPIO as GPIO
import time
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)
trig = 23
echo = 24
red = 17
green = 27
GPIO.setup(trig,GPIO.OUT)
GPIO.setup(echo,GPIO.IN)
GPIO.setup(red,GPIO.OUT)
GPIO.setup(green,GPIO.OUT)
GPIO.output(trig,GPIO.LOW)

try:
    while 1:
       GPIO.output(trig,GPIO.HIGH)
       time.sleep(0.00001)
       GPIO.output(trig,GPIO.LOW)
       while GPIO.input(echo)==0:
          pulse_start = time.time()
       while GPIO.input(echo)==1:
          pulse_end = time.time()
       pulse_duration = pulse_end - pulse_start
       distance = pulse_duration * 17150
       distance = round(distance, 2)
       print "Distance:",distance,"cm"
       time.sleep(0.5)
       if distance < 10:
          GPIO.output(red,GPIO.HIGH)
          GPIO.output(green,GPIO.LOW)
       else:
          GPIO.output(red,GPIO.LOW)
          GPIO.output(green,GPIO.HIGH)

except KeyboardInterrupt:
     GPIO.cleanup()
{% endhighlight %}

`$ sudo python ultrasonicLED.py`
