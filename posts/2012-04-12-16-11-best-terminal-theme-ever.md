> **Update** : checkout [Best terminal ever][1] for a slightly more advanced but better terminal guide.

#### Best Terminal Theme Ever

Adapted from [Noah Frederick's peppermint theme](http://noahfrederick.com/blog/2011/lion-terminal-theme-peppermint/).

##### Step 1

Download the peppermint theme from the link above.

##### Step 2: Enable Terminal Coloring

Enable some terminal coloring by adding the following lines to your `~/.bashrc` or `~/.bash_profile`

    COLOR_BOLD="\[\e[1m\]"
    COLOR_DEFAULT="\[\e[0m\]"
    PS1="$COLOR_BOLD\u@\h \w \$ $COLOR_DEFAULT"

#### Step 3: Git Coloring

Open up your terminal and paste the following line in: 

    git config --global --add color.ui true

And that's it, you're done. I didn't really like the default font for peppermint so I changed it back to menlo. Finally, I hit `command+=` twice to increase my font size and there you have it!

[1]:#