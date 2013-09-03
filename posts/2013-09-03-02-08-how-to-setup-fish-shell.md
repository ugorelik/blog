I've [always been a big fan of pimping out my console][old-guide]. Every time I see one of my coworkers' monochromatic green shell, I die a little inside.

For a while I was a big fan of [Noah Frederick's peppermint theme][old-theme] and I loved it, but then I discovered [Fish shell][fish]. *Fish shell is sweet, and it does a lot of nice things for you like colors, a fancy prompt, and nifty predictions*.

I've been using `fish` for a while now and I don't see myself going back to `bash` anytime soon.

### Installation

Fish shell can be a little daunting to install. I opted to install it from the source -- if you're comfortable with the terminal then do it this way. There's also a [package installer][fish-package] that you can use. 

To use fish, simple use the `fish` command.

``` bash
> fish
```

Once you're down with fish, make it your default shell: 

``` bash
chsh -s /usr/local/bin/fish
```

Or revert back to bash:

``` bash
chsh -s /bin/bash
```

There's a little gotcha, in order for the `chsh` command to work you have to have fish in your `/etc/shells`. You can read the [full details][stack-fish] cutesy of Nicholas Riley via StackOverflow. This is what mine looks like (note the addition of `/usr/local/bin/fish`):

``` bash
/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
/usr/local/bin/fish
```

Check out [how to use fish shell][how-to-fish] once it's ready.

[how to use fish shell]: /blog/how-to-use-fish-shell
[old-guide]: /blog/best-terminal-theme-ever
[old-theme]: http://noahfrederick.com/blog/2011/lion-terminal-theme-peppermint/
[fish]: http://ridiculousfish.com/shell/
[fish-package]: #
[stack-fish]: http://stackoverflow.com/questions/791227/unable-to-update-my-bash-in-mac-by-macports
