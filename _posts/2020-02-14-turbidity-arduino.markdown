---
layout: post
title: Turbidity Sensor အား Arduino ဖြင့် အသုံးပြုခြင်း
date: 2020-02-14 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: EPD/phoewa.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Displays]
---
Turbidity ဆိုသည်မှာ ရေထဲတွင်ရှိနေသော မျက်စိဖြင့် မြင်နိုင်/မမြင်နိုင်သော အရာဝတ္ထုပစ္စည်းများ (mainly suspended particles & colloids) များကြောင့် ဖြစ်ပေါ်လာသော ရေနောက်ကျိခြင်းကို ခေါ်ဆိုခြင်း ဖြစ်ပါတယ်။ Unit ကိုတော့ NTU (Nephelometric Turbidity Unit) နဲ့ တိုင်းတာကြပါတယ်။ ရေ၏သန့်ရှင်းမှုကို Turbidity ကို ကြည့်ပြီး အကြမ်းဖျဉ်း သိရှိနိုင်ပါတယ်။ ပြင်ပအရာဝတ္ထုပစ္စည်းများ ပျော်ဝင်မှုများလေ၊ ရေနောက်ကျိမှု Turbidity ပိုများလေ ဖြစ်ပါတယ်။ Turbidity ကို ဖြစ်စေတဲ့ အရာတွေကတော့ အဓိကအားဖြင့် –
(1) Phytoplankton လို့ ခေါ်တဲ့ အဏုဇီဝ ရေမှော်အပင်လေးများကြောင့်
(2) ရေမှော် ရေညှိပေါက်ပွားခြင်းကြောင့်
(3) ရေတိုက်စားခြင်းကြောင့် ဖြစ်ပေါ်လာတဲ့ အနယ်အနှစ်များကြောင့်
(4) ရေဆိုးစွန့်ထုတ်မှုများကြောင့်
(5) အိမ်သုံးရေစွန့်ထုတ်မှုများကြောင့် – စသည်တို့ကြောင့် အဓိက ဖြစ်ရပါတယ်။

<p align="center">
<img src="/assets/img/turbidity/clear.jpg">
</p>

### Turbidity များရင် ဘာဖြစ်နိုင်လဲ?

Turbidity ဖြစ်တဲ့ရေမှာ သတ္တဝါတွေ ရှင်သန်ဖို့ ခက်ခဲပါတယ်။ ရေပေါ်မှာရှိနေတဲ့ အမှုန်အမွှားတွေက နေရောင်ကို စုပ်ယူပြီး ရေရဲ့အပူချိန်ကို မြှင့်တင်ပါတယ်။ ရေအပူချိန်များလာတာနဲ့ oxygen ပျော်ဝင်နိုင်မှု နည်းလာပါတယ်။ ထို့ပြင် ရေထဲက အပင်များက နေရောင်အသုံးပြုပြီးစ ကာဗွန်ဒိုင်အောက်ဆိုဒ်ကနေ အစာချက်လုပ်တဲ့ Phytosynthesis လုပ်ငန်းကို လုပ်ဆောင်ပြီး ရေထဲကို oxygen ထုတ်လွှတ်ပေးပါတယ်။ ထို Phytosynthesis လုပ်ငန်းကို Highly turbid water မှာ အမှုန်အမွှားများက နေရောင်ခြည်ကို ဖုံးလွှမ်းထားလို့ အပင်များက လုပ်ငန်းလုပ်ဆောင်နိုင်ခြင်း မရှိတော့ပဲ ရေထဲက oxygen concentration ပိုနည်းလာပါတယ်။ Oxygen concentration ပိုနည်းပါးလာတဲ့ ရေမှာ သက်ရှိအပင်နဲ့ သတ္တဝါများ ရှင်သန်နိုင်မှု နည်းလာပြီး အချိန်ကြာမြင့်လာရင်တော့ Highly turbid water မှ Polluted water မျိုးအထိ ဖြစ်သွားနိုင်ပြီး အသုံးပြုဖို့ သင့်တော်ခြင်းမရှိတော့ပါဘူး။

<p align="center">
<img src="/assets/img/turbidity/muddy.jpg">
</p>

Turbidity များတဲ့ ရေကို သောက်သုံးရင်တော့ လူကို ဒုက္ခပေးနိုင်တဲ့ ဓာတ်သတ္တုပစ္စည်းများကို သောက်သုံးမိနိုင်ချေ အလွန်များပါတယ်။ WHO က သတ်မှတ်ထားတဲ့ 5NTU ထက် ပိုတဲ့ ရေကို မသောက်သုံးသင့်ပါဘူး။ ရေရှည်သောက်သုံးမိရင် အစာအိမ် အူလမ်းကြောင်းဆိုင်ရာ ပြဿနာများက စလို့ ကျန်းမာရေးကို ဆိုးဆိုးရွားရွားထိခိုက်တဲ့ထိ ဖြစ်နိုင်ပါတယ်။

Arduino အသုံးပြုပြီး ရေရဲ့ Turbidity ကို တိုင်းတာဖို့ DFRobot က ထုတ်တဲ့ sensor module ကို သုံးကြပါမယ်။ Sensor ဈေးနှုန်းကတော့ ၂သောင်း – ၂သောင်းခွဲကျပ် ဝန်းကျင်ရှိပါတယ်။ ကျွန်တော်ကတော့ စင်ကာပူ ES Online Shop က မှာယူပြီး ပို့ခမပါ ၂သောင်းခွဲကျပ် ကျသင့်ပါတယ်။ module မှာ Amplifier board တစ်ခုရယ် sensor ရယ် ပါပြီး၊ Sensor ရဲ့ အတွင်းထဲမှာ light transmitter နဲ့ receiver ပါဝင်ပါတယ်။ သန့်စင်တဲ့ရေမှာဆိုရင် transmitter မှ အလင်းဖြန့်ကြဲမှုနှုန်းဟာ နည်းမှာဖြစ်လို့ receiver မှ အလင်းပမာဏ အများစုကို လက်ခံရရှိမှာဖြစ်ပါတယ်။ ညစ်ညမ်းတဲ့ရေဆိုရင်တော့ light receiver ထဲကို အလင်းအနည်းငယ်သာ ပြန်မှာဖြစ်ပါတယ်။ Amplifier board ပေါ်မှာ “analog to digital” mode ပြောင်းလို့ရတဲ့ ခလုတ် ပါပါတယ်။ DFRobot ရဲ့ wiki မှာ ပြောထားတာကတော့ analog mode မှာ ခလုတ်ကို ထားရင် high turbidity ဖြစ်နေတဲ့ရေမှာ sensor ရဲ့ output value ဟာ လျော့ကျနေမှာဖြစ်ပြီး digital mode မှာတော့ output pin ဟာ high or low ဖြစ်နေပါလိမ့်မယ်။ digital mode မှာ ထားပြီး အဲ့ဒီ့ high/low level (trigger condition) ကို amplifier board ပေါ်မှာပါတဲ့ potentiometer (preset) လေးကို လှည့်ပြီး စိတ်ကြိုက် adjust လုပ်နိုင်ပါတယ်။ အတန်အသင့်ညစ်ညမ်းတဲ့ ရေနဲ့ ရေကြည်ကို 1 or 0 လို့ detect ချင်ရင်တော့ digital mode ကို သုံးလို့ အဆင်ပြေပြီး turbidity ရဲ့ level ကို ပြချင်ရင်တော့ analog mode သုံးသင့်ပါတယ်။

### Arduino သို့ Sensor pin များ ချိတ်ဆက်ခြင်း

<p align="center">
<img src="/assets/img/turbidity/wiring.jpg">
</p>

Amplifier board နဲ့ sensor နဲ့ ချိတ်ဆက်ရမယ့် ဝါနီနက် ကြိုးမှာ ကလစ်ပါတဲ့ဘက်ဟာ Sensor ဆီသို့ ချိတ်ရမှာဖြစ်ပါတယ်။ ဘက်မှားရင် sensor အလုပ်လုပ်မှာ မဟုတ်ပါဘူး။ Arduino ဆီသို့ ချိတ်ဆက်ရမယ့် ပြာနီနက် ကြိုးမှာ အပြာရောင်က data ၊ အနီရောင်က 5V ၊ အနက်ရောင်က Gnd pin တွေ ဖြစ်ပါတယ်။ DFRobot ရဲ့ wiki မှာ ထပ်ဖော်ပြထားတာက – ရေဟာ turbidity မရှိတဲ့ အခြေအနေမှာ sensor data pin မှ Voltage ဟာ 4.2V ဝန်းကျင် (0.00 NTU) ဖြစ်ပါတယ်။ ဒါပေမယ့် ကိုယ့် Sensor က သန့်စင်တဲ့ ရေမှာ 4.2V (0 NTU) မပေးတဲ့အခါ Sensor ရဲ့ waterproof ကော်အဖုံးလေးကို ဖွင့်ပြီး circuit ပြားပေါ်က Trimmer လေးကို လှည့်ပြီး ချိန်ညှိပေးရပါမယ်။ ကျွန်တော့်ရဲ့ Sensor ကို ဖွင့်ဖြုတ် ချိန်ညှိပြီး ကော်အဖုံးလေးထဲ ပြန်ထည့် တပ်လိုက်တဲ့အချိန်မှာ 4.2V မဟုတ်တော့ပဲ 3.8V တွေ ပြန်ဖြစ်ကုန်ပါတယ်။ ဒါကြောင့် ကျွန်တော်ကတော့ ကော်အဖုံးထဲကနေ Sensor ကို မထုတ်ပဲ Screw Driver ပိန်ပိန်ရှည်ရှည်နဲ့ ထိုးလှည့်ပါတယ်။

<p align="center">
<img src="/assets/img/turbidity/trimmer.jpg">
</p>

Sensor data တွေကို LCD မှာ ပြပေးတဲ့ Arduino Sketch ကတော့ အောက်ပါအတိုင်းဖြစ်ပါတယ်။ LCD မှာ 8bit I/O expander I2C module နဲ့ တွဲသုံးထားလို့ LiquidCrystal_I2C Library လိုအပ်ပါလိမ့်မယ်။

`Download – http://bit.ly/2Zrg7tQ`

{% highlight python %}
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

#define I2C_ADDR 0x27
#define BACKLIGHT_PIN 3
#define En_pin 2
#define Rw_pin  1
#define Rs_pin  0
#define D4_pin  4
#define D5_pin  5
#define D6_pin  6
#define D7_pin  7

LiquidCrystal_I2C  lcd(I2C_ADDR, En_pin, Rw_pin, Rs_pin, D4_pin, D5_pin, D6_pin, D7_pin);

int sensorPin = A0;
float volt;
float ntu;

void setup() {
  Serial.begin(9600);
  lcd.begin (16, 2);
  lcd.setBacklightPin(BACKLIGHT_PIN, NEGATIVE);
  lcd.setBacklight(LOW);
}

void loop() {
  volt = 0;
  for (int i = 0; i < 800; i++) {
    volt += ((float)analogRead(sensorPin) / 1023) * 5;
  }
  volt = volt / 800;
  volt = round_to_dp(volt, 1);
  if (volt < 2.5) {
    ntu = 3000;
  } else {
    ntu = -1120.4 * square(volt) + 5742.3 * volt - 4353.8;
  }
  Serial.print (volt);
  Serial.print (" V");
  Serial.print ("\t\t");
  Serial.print (ntu);
  Serial.println (" NTU");
  lcd.setCursor (0,0);
  lcd.print ("Voltage : ");
  lcd.print (volt);
  lcd.print ("V  ");
  lcd.setCursor (0,1);
  lcd.print ("Unit : ");
  lcd.print (ntu);
  lcd.print ("NTU  ");
  delay(10);
}
float round_to_dp( float in_value, int decimal_place ) {
  float multiplier = powf( 10.0f, decimal_place );
  in_value = roundf( in_value * multiplier ) / multiplier;
  return in_value;
}
{% endhighlight %}
