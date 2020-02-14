---
layout: post
title: E-Paper, E-Ink Display အသုံးပြုခြင်း
date: 2020-02-15 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: EPD/phoewa.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Displays]
---
E-Paper (Electronic paper) ကို Electrophoretic display လို့လည်း ခေါ်ဆိုပြီး display device အမျိုးအစားတစ်ခု ဖြစ်ပါတယ်။ E-ink (Electronic ink) လို့လည်း ခေါ်ဆိုကြပါတယ်။ အခြား display အမျိုးအစားတွေက အလင်းကို ထုတ်လွှတ်တာ ဖြစ်ပေမယ့် E-paper က စာရွက်ကဲ့သို့ အလင်းကို ရောင်ပြန်ဟပ်ပြီး မြင်ရစေတဲ့ display မျိုး ဖြစ်လို့ နေရောင်ထဲမှာတောင် display ပေါ်မှာပြထားတဲ့ ဒေတာ အချက်အလက်တွေကို ကောင်းစွာမြင်ရပါတယ်။ ဒါပေမယ့် E-paper နည်းပညာ က ဒေတာ ဖော်ပြတဲ့အခါ LCD ကဲ့သို့ low power display နည်းပညာတွေနဲ့ နှိုင်းယှဉ်ရင် refresh rate လွန်စွာနှေးလို့ mouse cursor blink တို့၊ စာသား scroll ပြခြင်းတို့လို fast moving ဖြစ်ရမယ့် အသုံးချနေရာတွေမှာဆို အဆင်မပြေပါဘူး။ ယခု အသုံးပြုမယ့် Waveshare ကထုတ်တဲ့ E-paper display module ဆိုရင် full refresh time က ၁၅စက္ကန့်တောင် ကြာပါတယ်။ Amazon က ထုတ်တဲ့ Kindle Tablet ကလည်း E-ink system ကို သုံးထားတဲ့ display အမျိုးအစားဖြစ်ပြီးတော့ ယခုအချိန်မှာ 67times per second အထိ refresh rate မြန်တဲ့ E-paper prototype တွေတောင် ထွက်ရှိနေပါပြီ။ 

![Electronic Shelf Labels]({{site.baseurl}}/assets/img/EPD/esl.jpg)

> ပုံ ၊ Electronic Shelf Labels

ဒါပေမယ့် E-paper display က Low Power Consumption ဖြစ်ခြင်း၊ 170° အထိ viewing angle ရှိခြင်း၊ အခြား display တွေနဲ့ မတူပဲ နေရောင်ပြင်းပြင်း အောက်မှာပင် ဒေတာအချက်အလက်တွေ မြင်ရနိုင်ခြင်း၊ display module ကို ပါဝါဖြုတ်လိုက်သော်လည်း ဖော်ပြထားတဲ့အချက်အလက်တွေ ကျန်ရှိနေခြင်း စတဲ့ အားသာချက်များစွာ ရှိပါတယ်။ အရွယ်အစားအမျိုးမျိုးရှိတဲ့ E-paper တွေကို Newspaper, E-book reader တွေသာမက digital photo frame တွေ၊ digital signage တွေ၊ information board တွေ အဖြစ် အသုံးပြုကြပြီး အထက်ပါပုံမှာ ဖော်ပြထားသလို အလွယ်တကူ ဈေးနှုန်း update လုပ်နိုင်တဲ့ Electronic Shelf Labels တွေ အဖြစ်လည်း အသုံးပြုကြပါတယ်။

![Electronic Papers]({{site.baseurl}}/assets/img/EPD/epd.jpg)

> ပုံ ၊ E-paper Display Module အရွယ်အစားအမျိုးမျိုး

E-paper display ကို Raspberry Pi နဲ့ ချိတ်ဆက်အသုံးပြုဖို့ Waveshare က ထုတ်တဲ့ display module အရွယ်အစားမျိုးစုံကို အသုံးပြုနိုင်ပြီး ယခု အသုံးပြု ပြသွားမှာက 296×128 pixels, 2.9inch အရွယ်အစားရှိတဲ့ E-paper display module ဖြစ်ပါတယ်။ SPI interface နဲ့ ချိတ်ဆက်ရမှာ ဖြစ်ပြီးတော့ display color အနေနဲ့ အနီရောင်၊ အနက်ရောင်နဲ့ နောက်ခံအဖြူရောင် ဖော်ပြနိုင်ပါတယ်။ Ultra low power consumption ဖြစ်ပြီး ပုံမှန်အားဖြင့် display refresh ပြုလုပ်တဲ့ အချိန်မှသာ 26.4mW ခန့်ပဲ သုံးစွဲပါတယ်။ Display Module ရဲ့ Pin တွေကို Raspberry Pi နဲ့ အောက်ပါအတိုင်း ချိတ်ဆက်ပေးရပါမယ်။

| E-Paper Display Module Pin  | Raspberry Pi Pin |
| ------------- | ------------- |
| BUSY  | BCM24 (Physical pin 18)  |
| RST  | BCM17 (Physical pin 11)  |
| DC  | BCM25 (Physical pin 22)  |
| CS  | 	CE0 (Physical pin 24)  |
| CLK  | SCLK (Physical pin 23)  |
| DIN  | MOSI (Physical pin 19)  |
| GND  | GND  |
| VCC  | 3.3V  |

ချိတ်ဆက်ပြီးရင် Waveshare E-paper အရွယ်အစားမျိုးစုံအတွက် Python Library တွေကို အောက်ပါ command အတိုင်း download ဆွဲယူထားလိုက်ပါ။

