---
id: 218
title: 'Hacker Notes: Git Branch in Shell Prompt'
date: 2011-09-02T15:05:35+00:00
author: dells
layout: post
guid: http://davidells.info/blog/?p=218
permalink: /2011/09/hacker-notes-git-branch-in-shell-prompt/
dsq_thread_id:
  - "402859984"
categories:
  - hacker-notes
---
[<img src="http://davidells.info/blog/wp-content/uploads/2011/09/git_branch_in_prompt1.png" alt="" title="git_branch_in_prompt" width="564" height="366" class="aligncenter size-full wp-image-257" />](http://davidells.info/blog/wp-content/uploads/2011/09/git_branch_in_prompt1.png)

Add this to the bottom of your .bash_profile or .bashrc
  
`#Add git info to prompt (attaching to working directory)<br />
function git_branch {<br />
  git branch --no-color 2> /dev/null | \<br />
        sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'<br />
}<br />
YELLOW="\[\033[0;33m\]"<br />
LIGHT_GRAY="\[\033[0;37m\]"<br />
PS1="$LIGHT_GRAY\h:\W $YELLOW\$(git_branch) $LIGHT_GRAY\u\$ "<br />
`