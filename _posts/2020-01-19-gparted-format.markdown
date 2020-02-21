---
layout: post
title: ၁.၃ SD card အား Gparted ဖြင့် format ချခြင်း
date: 2020-01-19 16:32:20 +0630
description: Raspberry Pi စာအုပ်
img: rpibook/raspberry-pi.jpg
fig-caption: # Add figcaption (optional)
tags: [Raspberry Pi, Book]
---
Raspbian OS တင်ပြီးသား SD card ကို အကြောင်းအမျိုးမျိုးကြောင့် Format ချလိုရင် Gparted ဆိုတဲ့ ဆော့ဝဲ သုံးလို့ ရပါတယ်။ Ubuntu Software Center မှာ Gparted လို့ ရိုက်ရှာပြီး install ထည့်သွင်းလို့ ရသလို terminal ကနေလည်း အောက်ပါ command နဲ့ install လို့ ရပါတယ်။

> $ sudo apt-get install gparted

<p align="center">
<img src="/assets/img/rpibook/gparted1.png">
<br>
<a>ပုံ(၁.၁၉) ၊ Ubuntu Software Center မှတဆင့် GParted ထည့်သွင်းခြင်း</a>
</p>

ထည့်သွင်းပြီးသွားရင် Gparted ကို ဖွင့်လိုက်ပါ။ ပုံ(၁.၂၀) ကအတိုင်း format ပြုလုပ်လိုတဲ့ ကိုယ့်ရဲ့ SD card ကို ရွေးပေးပါ။ အထက်မှာပြောခဲ့သလိုပဲ SD card ရဲ့ Partition ဟာ /dev/sdb ဖြစ်နေတာကို တွေ့ရပါမယ်။ ပုံ(၁.၂၁) မှာ သတိထားကြည့်လိုက်ရင် Right Click ထောက်ပြထားတဲ့ rootfs Partition က ဒုတိယ Partition /dev/sdb2 ဖြစ်ပြီး သူ့ရှေ့ကပ်လျက် အစိမ်းရောင်လေးက boot partition /dev/sdb1 ဖြစ်ပါတယ်။ ယခု နမူနာ လုပ်ပြနေတဲ့ SD card က 32GB ဖြစ်လို့ unallocated partition မှာ 25.45GB တောင် ဖြစ်နေတာ တွေ့ရပါတယ်။ ဒါကြောင့် SD card ရဲ့ Storage ကို အပြည့်အဝသုံးနိုင်အောင် ပုံ(၁.၁၈) တုန်းကလို Expand Filesystem ပြုလုပ်ရခြင်း ဖြစ်ပါတယ်။

<p align="center">
<img src="/assets/img/rpibook/gparted2.png">
<br>
<a>ပုံ(၁.၂၀) ၊ Gparted တွင် SD card ကို ရွေးချယ်ခြင်း</a>
</p>

Linux မှာ Partition တွေကို စီမံချင်ရင် ဒီအတိုင်းလုပ်လို့ မရပါဘူး။ SD card ရဲ့ partition တွေဟာ mount ဖြစ်မနေမှ ခွဲလို့ ရမှာပါ။ Right Click ထောက်ပြီး /dev/sdb1 ကော၊ /dev/sdb2 ပါ Unmount ပြုလုပ်ပေးလိုက်ပါ။ 

<p align="center">
<img src="/assets/img/rpibook/gparted3.png">
<br>
<a>ပုံ(၁.၂၁) ၊ partition ကို unmount ပြုလုပ်ခြင်း</a>
</p>

Unmount ဖြစ်သွားရင် Right Click ပြန်ထောက်ပြီး ၂ခုလုံးကို Delete လိုက်ပါ။

<p align="center">
<img src="/assets/img/rpibook/gparted4.png">
<br>
<a>ပုံ(၁.၂၂) ၊ Partition များ delete လုပ်ခြင်း</a>
</p>

SD card တစ်ခုလုံး unallocated ဖြစ်သွားရင် Partition အသစ် တည်ဆောက်ဖို့ Right Click နှိပ်ပြီး New ကို နှိပ်လိုက်ပါ။

<p align="center">
<img src="/assets/img/rpibook/gparted5.png">
<br>
<a>ပုံ(၁.၂၃) ၊ Partition အသစ် တည်ဆောက်ခြင်း</a>
</p>

ပေါ်လာတဲ့ box ထဲမှာ Partition တွေ ထပ်မခွဲပဲ Label နာမည်ပေးပြီး Add ကို နှိပ်လို့ရပါပြီ။ SD card ကို windows ကနေ Raspbian OS တင်ဖို့ အစီအစဉ်ရှိတယ် ဆိုရင်တော့ File System နေရာမှာ NTFS သို့မဟုတ် FAT32 ကို ရွေးခဲ့နိုင်ပါတယ်။ Ubuntu မှာပဲ သုံးမယ်ဆိုရင် ext4 က အဆင်ပြေပါတယ်။

<p align="center">
<img src="/assets/img/rpibook/gparted6.png">
<br>
<a>ပုံ(၁.၂၄) ၊ Partition Label name ပေးခြင်း</a>
</p>

New Partition ဖြစ်သွားပြီဆိုရင် အတည်ပြုဖို့ Apply အမှန်ခြစ်ကိုနှိပ်ပေးလိုက်ပါ။

<p align="center">
<img src="/assets/img/rpibook/gparted7.png">
<br>
<a>ပုံ(၁.၂၅) ၊ SD card အား ပြုပြင်ပြီးသမျှ အတည်ပြုခြင်း</a>
</p>

SD card Format ချဖို့ Gparted အပြင် Disks ဆိုတဲ့ Application လည်း သုံးနိုင်ပါတယ်။ Ubuntu မှာ Show Application Menu ကို နှိပ်ပြီး Utilities အောက်က Disks ကို ဖွင့်လိုက်ပါ။ ကိုယ့် SD card ကို ရွေးထားပြီးရင် Partition Volumes တွေ အောက်က အနှုတ်သင်္ကေတ ကို နှိပ်ပြီး delete ပြုလုပ် နိုင်ပါတယ်။

<p align="center">
<img src="/assets/img/rpibook/gparted8.png">
<br>
<a>ပုံ(၁.၂၆) ၊ Disks Application ဖြင့် format ပြုလုပ်ခြင်း</a>
</p>

unallocated ဖြစ်သွားရင် အပေါင်းသင်္ကေတကို နှိပ်ပြီး Volume နာမည်ပေးကာ Create ပြုလုပ်လိုက်ပါ။ Erase ကို ON ထားမိရင်တော့ အချိန်အတော်ကြာ စောင့်ရပါလိမ့်မယ်။

<p align="center">
<img src="/assets/img/rpibook/gparted9.png">
<br>
<a>ပုံ(၁.၂၇) ၊ SD card Volume Name သတ်မှတ်ပြီး Format ချခြင်း</a>
</p>

အခန်း(၁)အား ဆက်လက်ဖတ်ရှုရန် - <a style="text-decoration:none" href="https://kogyikaunghtet.github.io/cpu-temp/">၁.၄ CPU Temperature စစ်ဆေးခြင်း</a>
