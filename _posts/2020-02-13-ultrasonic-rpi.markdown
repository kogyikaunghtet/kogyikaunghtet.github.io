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
<img src="/assets/img/ultrasonic/muddy.jpg">
</p>

<center><img src="https://latex.codecogs.com/svg.latex?\Large&space;x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" title="\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" /></center>

