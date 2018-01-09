---
id: 144
title: 'Hacker Notes: Restart iChat'
date: 2011-08-19T03:02:59+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=144
permalink: /2011/08/hacker-notes-restart-ichat/
dsq_thread_id:
  - "390211175"
categories:
  - hacker-notes
tags:
  - applescript
  - ichat
---
<img src="http://davidells.info/blog/wp-content/uploads/2011/08/ichat.png" alt="" title="ichat" width="256" height="256" class="aligncenter size-full wp-image-153" />

I use iChat on the Mac for instant messenging at work. I like it fairly well, but tend to get disconnected randomly throughout the day. It might just be a symptom of a network problem, who knows. At any rate, it becomes a real distraction since I have to dismiss the message, find the window for that account, click the status area and set it back to &#8220;Available&#8221;.

I&#8217;ve always wondered why iChat doesn&#8217;t try to reconnect you when that happens. So I decided to make it work that way using the following applescript. I probably wouldn&#8217;t have thought twice about actually posting this, until I shared it with some folks at work who all really appreciated having it.

Here&#8217;s the code and steps to install:

`using terms from application "iChat"<br />
    on logout finished<br />
        delay 2<br />
        tell application "iChat"<br />
            log in of service "test@test.com"<br />
            #log in of service "more@test.com"<br />
        end tell<br />
    end logout finished<br />
end using terms from`

  1. Create a new file called ichat_restart.applescript and paste the above code into it
  2. Replace test@test.com with your email address and save the file (note if you have multiple accounts you can specify them with more &#8220;log in&#8221; statements like the one commented out)
  3. Open iChat, go to Preferences&#8230;
  4. Go to Alerts
  5. Select &#8220;When I Log Out&#8221; from the Event dropdown
  6. Select &#8220;Run an AppleScript script&#8221;
  7. Use the selector next to it and select &#8220;Choose script&#8230;&#8221;
  8. Select the file you created in step 1
  9. Once you save, try it out by manually changing your status to offline