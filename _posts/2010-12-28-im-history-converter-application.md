---
layout: post
title: IM History Converter Application
date: '2010-12-28T11:34:00.001+02:00'
tags: 
modified_time: '2010-12-28T11:37:58.044+02:00'
blogger_id: tag:blogger.com,1999:blog-7542889160674991776.post-5085892922446924810
blogger_orig_url: http://www.emil-genov.info/2010/12/im-history-converter-application.html
---

When transitioning to a new job, I got faced with problem of what to do with chat histories I have amassed in my last job. We have used pidgin for communication with jabber servers, and I have also used pidgin for my facebook chat, so all my work related history along with my private history was there.

I really wanted some central storage for this information. After pounding on solutions, I realized that it was there, already existing, waiting for me. Google stores it chat logs inside gmail. Wonderful idea, chats there are safe, easy accessible and what is most important completely search-able.

So I looked through Interwebs, for existing solution, but could not find one. Then I looked at format of pidgin history, and it was simple enough. Text file with each chat, and index files in xml.

I decided I will write this translator myself. Started with defining core objects, such as Contacts, IM Account and chat history logs. Also I decided to make it extensible for other input formats and also for other storage backends. Decision which plugin to use is taken in runtime based on configuration file or user entered parameters.

Gmail storage plugin uses IMAP to directly put chat histories as gmail messages with their original dates.

[So If anybody needs it, source code is available](https://code.google.com/p/im-history-converter/). On project page there are descriptions how to run the program. Also you can see how to make and run additional plugins to import chat from other systems. If anybody finds application useful, or have added additional plugins, please write a comment here or contact me on project page. Gracias
