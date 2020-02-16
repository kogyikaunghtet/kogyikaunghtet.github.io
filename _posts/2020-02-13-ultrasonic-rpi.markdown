---
layout: post
title: Ultrasonic Sensor အား Raspberry Pi ဖြင့် အသုံးပြုခြင်း
date: 2020-02-13 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: 
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Sensors]
---
HC-SR04 Ultrasonic Sensor က distance တိုင်းတာတဲ့နေရာတွေမှာ အသုံးပြုနိုင်ပြီး 2cm ကနေ 450cm အထိ တိုင်းတာနိုင်တဲ့အပြင် accuracy ကလည်း 3mm ခန့်သာ ဖြစ်လို့ အတော်တိကျကောင်းမွန်စွာ တိုင်းတာနိုင်ပါတယ်။ လူတွေ သာမာန်အားဖြင့် ကြားနိုင်တဲ့ အသံတွေက 20 to 20,000 Hz ကြားထဲမှာ ရှိပြီး 20Hz ထက် နည်းရင် infrasound ၊ 20,000Hz ထက် များရင် ultrasound လို့ ခေါ်ပါတယ်။ ultrasonic sensor က သူ့ရဲ့ transmitter မျက်လုံးလေး ဘက်ကနေ Ultrasound wave တစ်ခုကို ထုတ်လွှင့်ကာ obstacle သို့မဟုတ် solid object တစ်ခုခုကို ရိုက်ခတ်ပြီး ပြန်လာတဲ့ echo ပဲ့တင်သံကို receiver ဘက်ကနေ ပြန်ဖမ်းယူပါတယ်။ ဒီလို obstacle ကို သွားရိုက်ခတ်ပြီး ပြန်လာတဲ့ ကြာချိန် Pulse duration နဲ့ Ultrasound wave ရဲ့ Speed တို့ကို မြှောက်ခြင်း အားဖြင့် လိုချင်တဲ့ Distance တန်ဖိုးကို တွက်ထုတ်ယူရခြင်းပဲ ဖြစ်ပါတယ်။

<p align="center">
<img src="/assets/img/ultrasonic/hc-sr04.jpg">
<br>
<a>ပုံ၊ HC-SR04 Ultrasonic Sensor</a>
</p>

Ultrasonic Sensor ရဲ့ pin တွေကို ကြည့်ရင် Vcc, Trig, Echo, Gnd ဆိုပြီး ပင်၄ပင် တွေ့ရမှာဖြစ်ပါတယ်။ Trig (Trigger) က Ultrasound Wave တစ်ခု ထုတ်လွှင့်ပေးဖို့ pin ဖြစ်ပြီး ဒီ pin ကို အချိန်ကာလ တစ်ခုကြာအောင် High ပေးခြင်းအားဖြင့် ultrasound wave ကို ထုတ်လွှင့်နိုင်ပါတယ်။ Echo pin ကတော့ ပုံမှန် အခြေအနေမှာ LOW (0V) ရှိနေရမှာ ဖြစ်ပြီး sensor ရဲ့ transmitter ကနေ sound pulse တစ်ခုကို ထုတ်လွှင့်ပြီးနောက် echo pulse ပြန်ဝင်လာတဲ့ အချိန်မှာ High ဖြစ်သွားမှာ ဖြစ်ပါတယ်။ Low ဖြစ်နေတဲ့ အချိန်တန်ဖိုးထဲကနေ High ဖြစ်သွားတဲ့ အချိန်တန်ဖိုးကို နှုတ်ပေးခြင်းအားဖြင့် ပဲ့တင်သံ pulse ပြန်လာတဲ့ ကြာချိန် duration ကို တွက်ထုတ်ရမှာ ဖြစ်ပါတယ်။
Distance တွက်ထုတ်ဖို့ လိုအပ်တဲ့ pulse duration ကို သိရပြီဆိုရင် Speed of Sound တန်ဖိုးကိုတော့ ပျမ်းမျှ 343 m/s ကို ယူသုံးနိုင်ပါတယ်။ ဒီတန်ဖိုးက ပျမ်းမျှတန်ဖိုးသာ ဖြစ်ပြီး အပူချိန် 20°C ရှိတဲ့ ခြောက်သွေ့တဲ့ လေထုထဲက Speed of sound တန်ဖိုးသာ ဖြစ်ပါတယ်။ လေထုအပူချိန် အပြောင်းအလဲ၊ လေထုစိုထိုင်းဆ အတိုးအလျော့တွေပေါ်မူတည်ပြီး Speed of sound တန်ဖိုး ပြောင်းလဲနိုင်ပေမယ့် အနီးစပ်ဆုံးတန်ဖိုးဖြစ်တဲ့ 343 m/s ကိုပဲအသုံးပြုကြပါမယ်။ Unit ကိုတော့ cm (centimeter) နဲ့ပဲ ထွက်စေလိုတဲ့အတွက် ဒဿမတန်ဖိုး ၂လုံး ရွှေ့ရမှာ ဖြစ်လို့ 34300 cm/s ဖြစ်သွားပါမယ်။ ဒါပေမယ့် Echo pin ကနေ တွက်ထုတ်ပေးတဲ့ Pulse Duration ဟာ Transmitter ကနေ ultrasound wave ထွက်သွားပြီးနောက် obstacle ကို ရိုက်ခတ်ပြီး ပြန်လာတဲ့ အချိန်ကို ပေးနေတာ ဖြစ်လို့ Duration တန်ဖိုးက အသွား၁ဆ၊ အပြန်၁ဆ ဖြစ်နေပါတယ်။ ဒါကြောင့် Pulse Duration တန်ဖိုးကို ၂နဲ့ စားပေးရမှာ ဖြစ်ပြီး အောက်မှာ ပြသထားတဲ့ ညီမျှခြင်းအတိုင်း တွက်လိုက်ရင် Speed of Sound တန်ဖိုးက 17150 cm/s ကိုသာ ထည့်သုံးရတော့မှာ ဖြစ်ပါတယ်။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;34300=\frac{Distance}{Pulse Duration/2}" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>

<br>

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;17150=\frac{Distance}{Pulse Duration}" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>

Transmitter pin ဖြစ်တဲ့ Trig pin ကနေ Ultrasound Wave တစ်ခု ထုတ်လွှင့်ဖို့ အတွက်ကတော့ 0.1MHz တန်ဖိုးရှိတဲ့ Frequency Pulse တစ်ခု ထုတ်လွှတ် ပေးရင် လုံလောက်ပါတယ်။ Frequency ပုံသေနည်းအရ F=1/T ဖြစ်လို့ 10µs (0.00001 second) ခန့် High ပေးလိုက်ရင် 0.1MHz Frequency ထွက်ပါပြီ။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;Frequency=\frac{1}{0.00001 second}=0.1MHz" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>

Ultrasonic Sensor ကို Power Supply ပေးတဲ့အခါ သူ့ရဲ့ working voltage က 5V အပြည့်အဝ ရမှ အလုပ်လုပ်ဆောင်နိုင်တာဖြစ်လို့ Vcc ကို Raspberry Pi ရဲ့ 5V သို့ ချိတ်ဆက်ပေးရပါမယ်။ သို့ပေမယ့် Raspberry Pi ရဲ့ GPIO pin တွေက logic voltage 3.3V သာလျှင်ရှိတာကြောင့် သတိပြုရမယ့်အချက်တွေ ရှိပါတယ်။ Echo pin က sensor ကနေ output ထွက်မယ့် pin ဖြစ်ပြီး Raspberry Pi ဆီသို့ input signal အနေနဲ့ ဝင်မှာဖြစ်လို့ 5V signal pulse တွေ ဝင်ခိုင်းလို့ မရပါဘူး။ ဒါကြောင့် Raspberry Pi ရဲ့ GPIO pin ဆီကို ချိတ်ဆက်တဲ့အခါ အခန်း(၅)မှာ ဖော်ပြခဲ့သလိုမျိုး resistor ၂လုံး သုံးပြီး Potential divider တည်ဆောက်ကာ ချိတ်ဆက်ပေးရပါမယ်။ R1 တန်ဖိုးကို 1.5KΩ အသုံးပြုပြီး၊ R2 တန်ဖိုးကို 680Ω အသုံးပြုပါက 3.44V ဝန်းကျင်ရမှာ ဖြစ်လို့ Echo pin ကို Raspberry Pi ရဲ့ GPIO မှာ ချိတ်ဆက်ဖို့ အဆင်ပြေသွားပါလိမ့်မယ်။

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;V out=V in x \frac{R2}}{R1 + R2}" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>

<br>

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;V out=5V x\frac{1.5KΩ}}{680Ω + 1.5KΩ}=3.44V" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>
