---
id: 218
title: 'Hacker Notes: Git Branch in Shell Prompt'
date: 2011-09-02T15:05:35+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=218
permalink: /2011/09/hacker-notes-git-branch-in-shell-prompt/
img: 2011/09/git_branch_in_prompt1.png
dsq_thread_id:
  - "402859984"
categories:
  - hacker-notes
---

Add this to the bottom of your .bash_profile or .bashrc
  
{% highlight shell %}
#Add git info to prompt (attaching to working directory)
function git_branch {
  git branch --no-color 2> /dev/null | \
        sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
YELLOW="\[\033[0;33m\]"
LIGHT_GRAY="\[\033[0;37m\]"
PS1="$LIGHT_GRAY\h:\W $YELLOW\$(git_branch) $LIGHT_GRAY\u\$ "
{% endhighlight %}