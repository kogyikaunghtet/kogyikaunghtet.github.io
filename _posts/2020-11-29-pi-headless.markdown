---
layout: post
title: Raspberry Pi ကို Monitor မပါပဲ ဘယ်လို Setup လုပ်မလဲ?
date: 2020-11-29 13:32:20 +0630
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: headless/pi_setup.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, headless, network, setup]
---
Raspberry Pi ကို ပထမဆုံးအကြိမ်အဖြစ် စတင်အသုံးပြုမယ့် သူတွေအနေနဲ့ First Time Setup ပြုလုပ်ဖို့ ပုံမှန်အားဖြင့် Keyboard, Mouse, Monitor စသဖြင့် လိုအပ်လေ့ရှိပါတယ်။ ဒီလို Keyboard, Mouse, Monitor တွေ မချိတ်ဆက်ထားတဲ့ အချိန်မှာ တခြားကွန်ပျူတာ တစ်လုံး မှတဆင့် Raspberry Pi ကို Network ချိတ်ဆက်ပြီး ထိန်းချုပ်အသုံးပြုနိုင်ခြင်းကို “headless အသုံးပြုခြင်း” လို့ ေခါ်ပါတယ်။ headless ချိတ်ဆက်အသုံးပြုနိုင်ဖို့ လိုအပ်တဲ့ Remote Access အတွက် SSH (သို့မဟုတ်) VNC ဟာ Raspbian OS မှာ default အားဖြင့် disable ဖြစ်နေပါတယ်။ SSH ကို enable ပြုလုပ်ဖို့၊ Wifi ချိတ်ဆက်ဖို့နဲ့၊ Static IP address သတ်မှတ်ပြင်ဆင်ဖို့ Keyboard, Mouse, Monitor တွေ မရှိတဲ့အချိန်မှာ နက်ဝက်ကြိုး (Ethernet Cable) ရှိရုံနဲ့ First time setup ပြုလုပ်လို့ ရပါတယ်။

Raspbian OS download ရယူခြင်းနဲ့ SD card ပေါ်မှာ Raspbian OS တပ်ဆင်ခြင်း အတွက် ကိုတော့ ဒီနေရာ (https://kogyikaunghtet.github.io/sha-check/) မှာ ဖတ်ရှုနိုင်ပါတယ်။

Raspbian OS ကို SD card ပေါ်မှာ တင်ပြီးတဲ့နောက် ကွန်ပျူတာကနေ SD card ကို မဖြုတ်သေးပဲ /boot ဆိုတဲ့ directory ရဲ့ အောက်မှာ ssh ဆိုတဲ့ နာမည်နဲ့ ဖိုင်အလွတ်တစ်ခုကို ဖန်တီးပေးရပါမယ်။ ဒီလို ssh ဆိုတဲ့ ဖိုင်တစ်ခုကို /boot directory အောက်မှာ တည်ဆောက် ပေးလိုက်ခြင်းအားဖြင့် Raspbian OS ပထမဆုံးအကြိမ် boot တက်လာတဲ့ အခါမှာ SSH (Secure SHell) ကို enable ပြုလုပ်ပြီးသား ဖြစ်သွားစေပါတယ်။ ssh ဖိုင် တည်ဆောက်တဲ့ အခါ File Name မှာ “.txt” , “.exe” စသဖြင့် မည်သည့် file extension မျှ မပါဝင်စေရပါဘူး။

ကွန်ပျူတာမှာ Ubuntu OS အသုံးပြုသူများ အနေနဲ့ terminal မှာ အောက်ပါ command သုံးပြီး တည်ဆောက်နိုင်ပါတယ်။
`$ touch ssh`

Windows OS အသုံးပြုသူများကတော့ cmd မှာ အောက်ပါ command သုံးပြီး တည်ဆောက်နိုင်ပါတယ်။
`Type NUL >> ssh`

ပြီးတဲ့နောက်မှာတော့ ကွန်ပျူတာကနေ SD card ကို ဖြုတ်ပြီး Raspberry Pi ရဲ့ SD card slot မှာ တပ်ဆင်နိုင်ပါပြီ။ Raspberry Pi ရဲ့ Ethernet Port နဲ့ Laptop ရဲ့ Ethernet Port ကို RJ45 Ethernet Cable (နက်ဝက်ကြိုး) တစ်ချောင်း အသုံးပြုပြီး ချိတ်ဆက်ထားလိုက်ပါ။ ပြီးရင် Raspberry Pi ကို Power ပေးနိုင်ပါပြီ။

ကွန်ပျူတာမှာ Ubuntu OS သုံးသူများကတော့ Settings မှာ Wired Network ကို ဝင်ရောက်ပြီး IPv4 tab အောက်က Link-Local Only ကို ရွေးပေးထားဖို့ လိုအပ်ပါမယ်။

<p align="center">
<img src="/assets/img/headless/wired.png">
<br>
<a>ပုံ ၊ Wired Network Setting</a>
</p>

Wired Network Connected ဖြစ်သွားပြီဆိုရင် Terminal ကို ဖွင့်ပြီး အောက်ပါ command အတိုင်း SSH ဝင်ရောက်ချိတ်ဆက်နိုင်ပါပြီ။ Password ကတော့ First Time Setup ပြုလုပ်နေတာ ဖြစ်လို့ Raspberry Pi ရဲ့ Default Password ဖြစ်တဲ့ “raspberry” ကို ရိုက်ထည့်ပေးရမှာ ဖြစ်ပါတယ်။

`$ ssh pi@raspberrypi.local`

<p align="center">
<img src="/assets/img/headless/pilocal.png">
<br>
<a>ပုံ ၊ SSH ချိတ်ဆက်ခြင်း</a>
</p>

Windows OS သုံးပြီး First Time Setup ပြုလုပ်တဲ့ သူများအတွက်ကတော့ ကွန်ပျူတာမှာ Network setting တွေ ပြုပြင်နေစရာ မလိုအပ်ပါဘူး။ SSH ဝင်ရောက်ဖို့အတွက်ကတော့ Putty (https://www.putty.org/) Software အသုံးပြုပြီး ဝင်ရောက်နိုင်ပါတယ်။

<p align="center">
<img src="/assets/img/headless/putty.png">
<br>
<a>ပုံ ၊ Putty မှတဆင့် SSH ချိတ်ဆက်ဝင်ရောက်ခြင်း</a>
</p>

Raspberry Pi ကို ကွန်ပျူတာနဲ့ အထက်ပါနည်းလမ်းတွေအတိုင်း အဆင်ပြေပြေ ဝင်ရောက် ချိတ်ဆက်နိုင်ပြီဆိုရင် Wifi Setting သတ်မှတ်ပြင်ဆင် ချိတ်ဆက်ကြပါမယ်။ Ethernet Cable အသုံးပြုပြီး headless ချိတ်ဆက်တဲ့အခါ Raspberry Pi မှာ Wifi block ဖြစ်နေတတ်ပါတယ်။ အောက်ပါ command နဲ့ wifi ကို unblock ပြုလုပ်နိုင်ပါတယ်။

`$ sudo rfkill unblock wifi`

Raspberry Pi ကို ပါဝါပေးပြီးနောက် Raspbian OS တက်လာတဲ့အချိန်မှာ ကိုယ် ချိတ်ဆက်စေလိုတဲ့ wifi ကို အလိုအလျောက် connect ဖြစ်စေဖို့၊ multiple wifi network အချက်အလက်တွေ ဖြည့်သွင်းထားပြီး ပထမ ဦးစားပေး၊ ဒုတိယ ဦးစားပေး ချိတ်ဆက်နိုင်စေဖို့နဲ့ hidden ဖြစ်နေတဲ့ wifi network တွေကို ချိတ်နိုင်ဖို့ wpa_supplicant Configuration File ထဲမှာ သတ်မှတ် ပြင်ဆင် ထားနိုင်ပါတယ်။ nano text editor အသုံးပြုပြီး wpa_supplicant.conf ကို အောက်ပါ command အတိုင်း ဖွင့်လိုက်ပါ။

`$ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`

Default အနေနဲ့ wpa_supplicant.conf ဖိုင်ရဲ့ အပေါ်ဆုံးမှာ အောက်ပါလိုင်း ၂လိုင်း ရှိနေပါလိမ့်မယ်။

{% highlight shell %}
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
{% endhighlight %}

ဒီ၂လိုင်းရဲ့ အောက်ဆုံးမှာ ကိုယ်ချိတ်ဆက်မယ့် wifi network ရဲ့ SSID နဲ့ Password ကို အောက်ပါအတိုင်း ဖြည့်သွင်းပေးရပါမယ်။ ဖြည့်သွင်းပြီးရင် Ctrl+X နဲ့ ထွက်ပြီး၊ save ပြုလုပ်ရန် Y ရိုက်ကာ Enter ခေါက်ပေးပါ။

{% highlight shell %}
network={
    ssid="YourNetworkSSID"
    psk="YourPassword"
    key_mgmt=WPA-PSK
}
{% endhighlight %}

တကယ်လို့ wifi က password မသတ်မှတ်ထားဘူးဆိုရင် key_mgmt နေရာမှာ အောက်ပါအတိုင်း NONE လို့ ထားခဲ့နိုင်ပါတယ်။

{% highlight shell %}
network={
    ssid="YourNetworkSSID"
    key_mgmt=NONE
}
{% endhighlight %}

Wifi Router မှာ SSID Visibility ကို ပိတ်ထားလို့ Hidden ဖြစ်နေတဲ့ wifi network ကို ချိတ်ဆက်လိုတယ်ဆိုရင်တော့ scan_ssid=1 လို့ ထည့်ပေးရပါမယ်။

{% highlight shell %}
network={
    ssid="YourHiddenNetworkSSID"
    scan_ssid=1
    psk="YourPassword"
}
{% endhighlight %}

wpa_supplicant.conf မှာ wifi network အချက်အလက် ၂ခု ထည့်ပြီး multiple configuration လည်း setup ပြုလုပ်ထားနိုင်ပါတယ်။ နမူနာအနေနဲ့ ကျောင်းရဲ့ wifi အတွက် တစ်ခု၊ အိမ်က wifi အတွက် တစ်ခု သတ်မှတ်ထားလိုတယ် ဆိုရင် အောက်ပါအတိုင်း network details ကို ၂ခု ထည့်လိုက်ရုံပါပဲ။

{% highlight shell %}
network={
    ssid="SchoolNetworkSSID"
    psk="SchoolPassword"
    id_str="school"
}
network={
    ssid="HomeNetworkSSID"
    psk="HomePassword"
    id_str="home"
}
{% endhighlight %}

တကယ်လို့ ကိုယ့် wifi range အတွင်းမှာ ချိတ်ဆက်လို့ ရတဲ့ wifi network ၂ခု ရှိနေရင် ပထမဦးစားပေးပြီး ချိတ်စေလိုတဲ့ wifi နဲ့၊ ဒုတိယဦးစားပေး wifi ကို အောက်ပါအတိုင်း priority သတ်မှတ်နိုင်ပါတယ်။

{% highlight shell %}
network={
    ssid="FirstSSID"
    psk="FirstPassword"
    priority=1
    id_str="firstSSID"
}
network={
    ssid="SecondSSID"
    psk="SecondPassword"
    priority=2
    id_str="secondSSID"
}
{% endhighlight %}

Raspberry Pi 3 Model B+ နဲ့ အထက် version တွေမှာ Country Code ကိုလည်း wpa_supplicant.conf မှာ ထည့်သွင်းပေးထားဖို့ လိုအပ်ပါမယ်။ UK အတွက် GB ဖြစ်ပြီး၊ မြန်မာနိုင်ငံအတွက်ကိုတော့ MM လို့ ထည့်နိုင်ပါတယ်။ Configuration file setup အပြည့်အစုံကတော့ အောက်ပါအတိုင်း ဖြစ်ပါတယ်။

{% highlight shell %}
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=MM
network={
    ssid="YourNetworkSSID"
    psk="YourPassword"
    key_mgmt=WPA-PSK
}
{% endhighlight %}

လိုအပ်တဲ့ Wifi Setting တွေ သတ်မှတ်ပြင်ဆင်ပြီးတဲ့နောက်မှာ Raspberry Pi ကို restart ချလိုက်ရင် စက်ပြန်တက်လာတဲ့အခါ wifi ကို အလိုအလျောက် ချိတ်ဆက်သွားပါလိမ့်မယ်။


