---
layout: post
title: Fixing problem with missing EXIF information in photos sent in whatsapp 
date: '2016-11-15T19:00:00.000+02:00'
tags: exif,photos,ubuntu,shotwell
---

I'm using excelent app [Shotwell](https://wiki.gnome.org/Apps/Shotwell) on ubuntu, in order to classify my fotos by periods that they were taken. Recently I run into problem that all photos I received through whatsapp, entered in unknown date bucket. I investigated and found out that it is because Shotwell classifies them using createDate from EXIF data of jpeg files. Unfortunately whatsapp strips this data, so images can not be classified. 

Enter excelent tool: [exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool/). To install it run:
```$ sudo apt-get install libimage-exiftool-perl```

After that run following commands into the folder where you have you photos with wrong date:

    exiftool -P "-FileName>AllDates" -overwrite_original -if '(not $datetimeoriginal or ($datetimeoriginal eq "0000:00:00 00:00:00"))' *
    exiftool -P "-FileModifyDate>AllDates" -overwrite_original -if '(not $datetimeoriginal or ($datetimeoriginal eq "0000:00:00 00:00:00"))' *


The first command will parse filenames to get date/time stamp and put it into EXIF header, for all files that have missing dateTimeOriginal in their EXIF.
The second one will do the same for the ones that couldn't be parsed but by using file modify date from linux

To see what flags are doing, you can go through excelent [FAQ of exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool/faq.html)

Then you should close Shotwell, drop it's database:
```
rm -fr ~/.local/share/shotwell/
rm -fr ~/.cache/shotwell/
```

and then restart it and reimport photos, now they will be with their correct dates.
