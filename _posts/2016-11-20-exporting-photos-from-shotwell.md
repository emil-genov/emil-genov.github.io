---
layout: post
title: Exporting photos from Shotwell 
date: '2016-11-20T19:00:00.000+02:00'
tags: exif,photos,ubuntu,shotwell
---

I'm using excelent app [Shotwell](https://wiki.gnome.org/Apps/Shotwell) on ubuntu, in order to classify my fotos by periods that they were taken. Unfortunately it does not allow you to export such classified albums. I found a [very usefull script writen by Robert Koehler](https://bitbucket.org/robertkoehler/shotwell-export)

It basically reads internal sqlite db of shotwell and creates an export of all photos separating it in folders based on Shotwell events. It had only one shortcomming for me. If you have photos that you like to keep, but you do not want to create album for them you can leave the default empty name of Shotwell event. But export script then still creates folder for them. My desired behaviour for this cases is to just leave them in the base export directory, without creating folder for them. [So I forked his project and implemented exactly this behaviour.](https://github.com/emil-genov/shotwell-export)

Hope is usefull for somebody.
