# My Setup - Development on OS X

A lot of my friends and colleagues tend to turn to me when they need advice on good software for OS X.
I've used OS X for many years now, both personally and professionally, and have always felt the need to improve my workflow and the tools I use, so I've tested _a lot_ of stuff out there.
A colleague of mine suggested I do a write-up of how I setup my machine and here we are.
This is mostly targeted for a development machine, but I use the exact same setup for my personal machines too.

## Setup

### Homebrew

The first thing I install on any machine is [homebrew](https://github.com/homebrew/homebrew), it's a 3rd party package manager which enables me to easily install much needed tools.

### Homebrew packages

I'll list the most essential packages from homebrew:

* [_git_](http://git-scm.com/) I use `git` for all my personal projects;
 every little thing becomes a git repository and thus I have versions of everything.
* [_hub_](https://github.com/github/hub) `hub` is an extension of `git` for [github](https://github.com).
With this tool you can easily fork and clone repositories and make pull requests, all from your terminal.
* [_autojump_](https://github.com/joelthelion/autojump) It's a shell utility tool for easier directory switching.
It builds an index of which directories you visit most and then offers switching directories by fuzzy-matching search terms: `j <search-term>`
* [_coreutils_](http://www.gnu.org/software/coreutils/) The best friend for all Linux -nerds.
This installs the GNU versions of popular tools like `ls`, `cp` etc. linking these tools correctly removes all the confusion between the BSD and Linux versions.
* [_vim_](http://www.vim.org/) There just has to be a powerful text based editor installed for your terminal editing needs, I prefer `vim`.
* [_wget_](https://www.gnu.org/software/wget/) Because really, `wget google.com` is easier than `curl -o foo google.com`.
* [_httpie_](http://httpie.org) I'm tired of having to remember all the necessary flags for `curl`, `httpie` makes life easy: `http POST foo.com bar=1 baz=2`.
* [_peco_](https://github.com/peco/peco) `peco` offers fuzzy-searching from STDIN.
For example: `ls -l | peco`. It is most useful when piping output to other commands: `ps -fae | peco | awk '{ print $2; }' | xargs kill -9`.
This allows me to search for and kill a process.
* [_zsh_](http://www.zsh.org/) I happen to like `zsh` more than `bash`.
This is more of a personal preference though.
* [_brew-cask_](https://github.com/caskroom/homebrew-cask) Is an addition to `homebrew` for installing apps.
`homebrew` doesn't allow packages which install apps and thus `brew-cask` was created.

### Applications

Next up are the most essential apps (which can all be installed with `brew-cask`):

* [_alfred_](http://www.alfredapp.com/) `Spotlight` is a pretty decent finder, but `Alfred` or `Quicksilver` are absolutely top notch in finding the stuff you need from your machine.
They also include lots of customization options and extensions to integrate better into your workflow.
* [_QuickLook extensions_](https://github.com/sindresorhus/quick-look-plugins) `QuickLook` in itself is a bit flawed, but luckily it is somewhat extensible.
Ever wanted to just see what that README file contains?
Install [`qlstephen`](http://whomwah.github.io/qlstephen/), it enables `QuickLook` to show all extensionless files as plain text.
Using a lot of markdown and would like to see the actual rendered output?
Use [`qlmarkdown`](https://github.com/toland/qlmarkdown).
We're coders and we like to look at code files with some form of syntax highlighting, so use [`qlcolorcode`](https://code.google.com/p/qlcolorcode/).
 How about formatted JSON?
 Use [`quicklook-json`](http://www.sagtau.com/quicklookjson.html), and for CSV there is [`quicklook-csv`](https://github.com/p2/quicklook-csv).
 Ever wanted to see what that ZIP file includes, without extracting it or jumping to the terminal? [`betterzipql`](http://macitbetter.com/BetterZip-Quick-Look-Generator/) got your back.
 A lot of OS X stuff comes in installer packages, and maybe you want to investigate what the package contains, before running it?
 Use [`suspicious-package`](http://www.mothersruin.com/software/SuspiciousPackage/).
 `brew-cask` makes handling `QuickLook` plugins easy, manually they are a bit of a hassle.
* [_Amethyst_](https://github.com/ianyh/Amethyst) I've recently become enlightened and have begun using a tiled "window manager" for OS X;
 there's just something beautiful about all your windows filling the whole screen estate automatically.
 Also, handy shortcuts allow you to "throw" windows to other Desktops and other Screens.
* [_Fluid_](http://fluidapp.com/) Are there websites you use a lot?
Do you wish you could have `stackoverflow.com` as an app?
`Fluid` can make any website into and application.
Currently I use `Fluid` for <http://omniref.com> and <http://devdocs.io>
* [_iTerm2_](http://iterm2.com/) There's nothing awfully wrong about using the default `Terminal`, but I find that `iTerm2` just packs a lot more punch: proper tabs, shortcuts for splitting views, `tmux` support, etc.
* [_SourceTree_](http://www.sourcetreeapp.com/) I mostly use `git` from the terminal, but looking at branches and diffs in the terminal isn't just efficient enough, so a good GUI for `git` is needed and Atlassian has done a really good job with this one - it's even platform independent.
Currently it's the best free solution on the market, though `Github for Mac` is becoming better by the day.
* [_atom_](https://atom.io/) Again, a proper editor is necessary.
I used to roll with `Sublime Text 2` before this, but since last year I've migrated to `Atom`.
An editor which is free and open-source, with an active community and development team?
Hells yes!
It's fully extendable, with it's extensions written in JavaScript, and the core team has no problem with accepting pull requests.
* [_Google Chrome_](http://www.google.com/chrome/) I usually install `Opera`, `Firefox`, `Safari` and `Chrome` but for my day-to-day use, it's `Chrome`.
There are many extensions and features which I couldn't live without and it isn't even that bad of a browser, maybe a bit memory heavy (and lacks the damn workspaces from Firefox, and even they stopped using them :frowning: )

### Terminal configuration

The last step in my setup (in the scope of this post) is to configure my terminal.
I install `pip` to handle python packages and with it, I `pip install powerline-status`. [Powerline](https://github.com/powerline/powerline) is a statusline modification for `vim` and your shell, which is pretty extensible and allows for a lot of information on the - you guessed it - statusline.
I've configured it to show machine load, current VCS branch, status code of last command, current user, working directory path and whether I'm in INSERT or COMMAND mode (yeah, I use the shell in `vim` mode).

And for the rest of the configuration I just symlink all the necessary files like `.zshrc`, `.gitconfig` from my git repository (like I said, I use a git repository for most anything :)) which holds all my [dotfiles](https://github.com/deiga/dotfiles).
This allows me to easily deploy my configs to a new machine.

This repository actually includes a `Rakefile` which handles all the setup I've described here.
All I need on a new machine is to fetch the repository from `github.com`, have `ruby` and `rake` installed and then I can install everything with `rake install`.
This is of course way too much 'pre-setup', so I'm working on a script to handle the setup and installation on its own.

## Apps worth mentioning

There are loads of apps which I use and which are mostly necessary on a personal level.

Two apps I can't live without are [Karabiner](https://pqrs.org/osx/karabiner/) and [Seil](https://pqrs.org/osx/karabiner/seil.html.en), they allow me to remap keys on my keyboard and thus work a lot faster.

I've completely removed <kbd>CAPSLOCK</kbd> functionality from my keyboard and instead the key acts as <kbd>ESC</kbd> when pressed for a short time and <kbd>CONTROL</kbd> when pressed for a long time.
I've also changed my <kbd>SHIFT</kbd> keys to produce left and right braces, respectively, on short presses.
I've also bound all modifiers to the actual <kbd>CTRL</kbd> key, to resemble the <kbd>HYPER</kbd> modifier of the old [Space Cadet keyboard](http://world.std.com/~jdostale/kbd/SpaceCadet.html).

[ControlPlane](http://www.controlplaneapp.com/) Is an app which can determine contexts based on location, time of day, etc.
These context can close apps, set sound level, start apps and a whole lot of useful actions.
I've set it up to lock my screen when I'm not at my laptop, when outside my home and to close all unnecessary battery draining apps when on battery power. These are just a few examples of what it can do.
