# My Setup - Development on OS X

A lot of my friends and colleagues tend to turn to me when they need advice on good software for OS X. I've used OS X for many years now, both personally and professionally, and have always felt the need to improve my workflow and the tools I use, so I've tested _a lot_ of stuff out there. A colleague of mine suggested I do a write-up of how I setup my machine and here we are. This is mostly targeted for a development machine, but I use the exact same setup for my personal machines too.

## Setup

### Homebrew

The first thing I install on any machine is [homebrew](https://github.com/homebrew/homebrew), it's a 3rd party package manager which enables me to easily install much needed tools.

### Homebrew packages

I'll list the most essential packages (for my workflow) from homebrew next:

* _git_ I use `git` for all my personal project, every little thing becomes a git repository and thus I have versions of everything.
* _hub_ `hub` is an extension for `git` for [github](https://github.com). With this tool you can easily fork and clone repositories and make pull-requests, all from your CLI
* _autojump_ It's a shell utility tool for easier directory switching. It builds an index of which directories you visit most and then offers fuzzy-matching directories with `j <search-term>`
* _coreutils_ The best friend for all Linux -nerds. This installs the GNU versions of popular tools like `ls`, `cp` etc. Linking these tools correctly removes all the confusion between BSD and Linux versions of these tools.
* _vim_ There just has to be a powerful text based editor installed for your CLI editing needs, I prefer `vim`
* _wget_ Because really, `wget foo` is easier than `curl -O foo foo`
* _httpie_ I'm tired of having to remember all the necessary flags for `curl`, `httpie` makes life easy: `http POST foo.com bar=1 baz=2`
* _peco_ `peco` offers fuzzy-searching from STDIN (`ls -l | peco`) for example for piping stuff forward (`ps -fae | peco | awk '{ print $2; }' | xargs kill -9` This allows me to search for a process, I want to kill, with `peco`)
* _zsh_ I happen to like `zsh` more than `bash` this is more personal preference
* _brew-cask_ Is an addition to `homebrew` for installing apps. `homebrew` doesn't allow packages which install apps and thus `brew-cask` was created.

### Applications

Next up are the most essential apps (which can all be installed from `brew-cask`):

* _alfred_ Spotlight is a pretty decent finder, but `Alfred` or `Quicksilver` are absolutely top notch in finding the stuff you need from your machine. They also include lots of customization options and extensions to integrate better into your workflow
* _QuickLook extensions_ QuickLook in itself is a bit flawed, but luckily it is somewhat extensible. Ever wanted to just see what that README file has in it? Install `qlstephen`, it enables quicklook to show all extensionless files as text. Using a lot of markdown and would like to see the actual rendered output? Use `qlmarkdown`. We're coders and we like to look at code files with some form of syntax hilighting, so use `qlcolorcode`. How about formatted JSON? Use `quicklook-json`, and for CSV there is `quicklook-csv`. Ever wanted to see what that ZIP file includes, without extracting it or jumping to the terminal? `betterzipql` got your back. A lot of OS X stuff comes in installer packages, maybe you want to investigate what the package has in it, before running it? Use `suspicious-package`. `brew-cask` makes handling QuickLook plugins easy, manually they are a bit of a hassle...
* _Amethyst_ I've recently become enlightened and have begun using a tiled "window manager" for OS X, there's just something beatiful about all your windows filling the whole screen estate automatically. Also, handy shortcuts allow you to "throw" windows to other Desktops and other Screens.
* _Fluid_ Are there websites you use a lot? Do you wish you could have `stackoverflow.com` as an app? `Fluid` can make any website into and application. Currently I use `Fluid` for `omniref.com` and `devdocs.io`
* _iTerm2_ There's nothing much wrong about using `Terminal`, but I find that `iTerm2` just packs a lot more punch: proper tabs, shortcuts for splitting views, `tmux` support, etc.
* _SourceTree_ I use `git` from the CLI mostly, but looking at branches and diffs on the CLI isn't just efficient enough, so a good GUI for `git` is needed and Atlassian has done a really good job with this one, it's even platform independent. Currently it's the best free solution on the market, though `Githbu for Mac` is becoming better by the minute.
* _atom_ Again, a proper editor is necessary. I used to roll with `Sublime Text 2` before this, but since last year I've migrated to `Atom`. An editro which is free and open-source, with an active community and development team? Hells, yes! It's fully extendable, it's extensions are written in JavaScript and the core team has no problem with accepting PR's
* _Google Chrome_ I usually install `Opera`, `Firefox`, `Safari` and `Chrome` but my day-to-day use falls into `Chrome`. There are many extensions and features which I couldn't live without and it isn't even that bad of a browser, maybe a bit memory heavy (and lacks the damn workspaces from Firefox, and even they stopped using them :( )

### CLI configuration

The last step in my setup (in the scope of this post) is to configure my CLI. I install `pip` to handle python packages and with it, I install `powerline-status`. Powerline is a statusline modification for `vim` and your shell, which is pretty extensible and allows for a lot of information on the statusline. For me it shows machine load, current VCS branch, status code of last command, current user, workind directory path and wheter I'm in INSERT or COMMAND mode (yeah, I use the shell in `vim` mode).

And for the rest of the configuration I just symlink all the necessary files like `.zshrc`, `.gitconfig`, etc.
I use a git repository (like I said, I use a git repository for most anything :)) for all my [dotfiles](https://github.com/deiga/dotfiles) which allows me to easily deploy my configs to a new machine.

This repository actually includes an `Rakefile` which handles all the setup I've described here. All I need on a new machine is to fetch the repository from `github.com`, have `ruby` and `rake` installed and then I can install everything with `rake install`. This is of course way too much 'pre-setup', so I'm working on a script to handle the setup and installation on its own.


## Apps worth mentioning

There are loads of Apps which I use and which are mostly necessary on a personal level.

Two apps I can't live without are [Karabiner]() and [Seil](), they allow me to remap keys on my keyboard and thus work a lot faster.
I've completely removed CAPSLOCK from my keyboards and instead the key acts as ESC when pressed a short time and CONTROL when pressed as long time. I've also changed my SHIFT keys to produce left and right braces respectively on short presses. I've also bound all modifiers to the actualy `ctrl` key, to resemble the HYPER modifier of old.

[ControlPlane]()
