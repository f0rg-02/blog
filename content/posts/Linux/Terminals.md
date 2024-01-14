+++
title = 'Terminals'
date = 2024-01-14T15:45:21-05:00
draft = false
+++

**NOTE: I decided to add both links and also paste configs. So there is a lot of "useless" stuff in here, but I think having a variety is important.**

------
## <u>My Scattered Thoughts:</u>

I love Linux. You can do anything with it, but most importantly that there are usually many options for one thing like terminals that there is something for everyone. After way too many times spent on computers (I really should go outside more, but the weather is shit right now), I've come up with a workflow and environment that works for me. Even though I'm constantly tweaking and modifying my setups to this day, I have found things that I prefer over others. One of these are terminals. I've probably tried every single terminal that I could find. My criteria is usually very simple, lightweight and pretty customization. Of course I don't use every single feature of the terminals I usually use and I try to make it "pretty", but this isn't a necessity since making it pretty usually relies on if it is easier on my eyes and more of usability than just using an over bloated pile of on fire garbage. Anyways, enough ranting and my coffee is still kicking in, but here is what works for me and what I've learned over the years.

------

## <u>The beginning:</u>

When I first started running and using Linux, I didn't understand how to customize my Linux install to get rid of the annoying bloatware and other annoyances, but as I got annoyed with DE's like GNOME and KDE with their crap environments, I've used a combination of search engines and way too many hours spent breaking Linux. Now, I finally figured out operating systems that I prefer for what tasks and also programs and utils that I also prefer over others.

For terminals I currently use a combination of Tmux, Tilix, urxvt, and most recently kitty. When I was setting up my Desktop, since I didn't have the battery or my laptop being bogged down by bloat, I had more freedom to try out more programs that could take up more resources depending on what I was doing. 

------
#### <u>kitty:</u>

I decided to give kitty and try. At first it was ugly and pretty much useless for me, but after a bit of reading and ripping configs, I've managed to get it a bit more customized and figured out some of the keyboard shortcuts that I would use. The documentation is better than most: https://sw.kovidgoyal.net/kitty/overview/ and is definitely a must to be read, but I mostly just used it for shortcuts and figuring out where the config is supposed to be (I have mine in `~/.config/kitty/kitty.conf`)

Now my current kitty config:

```ruby
foreground #a9b1d6
background #1a1b26
cursor #a9b1d6

color0 #1a1b26
color8 #4e5173

color1 #F7768E
color9 #F7768E

color2 #9ECE6A
color10 #9ECE6A

color3 #E0AF68
color11 #E0AF68

color4 #7AA2F7
color12 #7AA2F7

color5 #9a7ecc
color13 #9a7ecc

color6 #4abaaf
color14 #4abaaf

color7 #acb0d0
color15 #acb0d0


# Cursor
cursor_shape     							underline
cursor_blink_interval     					-1
cursor_stop_blinking_after 			15.0

# Scrollback
scrollback_lines 							10000

# Window
remember_window_size   				no
initial_window_width   					1000
initial_window_height  					400
window_border_width 					0
window_margin_width 					12
window_padding_width 					10
inactive_text_alpha 						1.0
background_opacity 						.95
placement_strategy 						center
hide_window_decorations 				no
```

It works for what I want and matches the "theme" of my xfce4 desktop environment. I only really use this on my desktop. On my laptop I did switch to this config and kitty from urxvt, but I will probably switch back to urxvt which is another terminal that when configured is pretty neat. The only reason I switched to kitty was because of ohmyphosh wasn't showing the glyphs of the "icons", but on my laptop I will probably switch to a minimal theme and change the terminal back to urxvt. That configuration came mostly from this openbox wm dotfiles: https://github.com/owl4ce/dotfiles

------
#### <u>urxvt:</u>

This terminal requires configuration, but after a bit of tweaking and messing around, it is very good and has a lot of features all offered in a lightweight format.

urxvt has been configured to fit my needs and yes, I use configs posted on github because time is money and I just want a nice environment setup and working, but anyways, for urxvt you edit `~/.Xresources` file to configure your terminal and after everything change, you have to run `xrdb ~/.Xresources` instead of logging in and out. The default config for the dotfiles are here: https://github.com/owl4ce/dotfiles/blob/ng/.Xresources

It is beautiful. The config pasted is:

```ruby

! X resource database.
! https://github.com/owl4ce/dotfiles

! URxvt configuration.
URxvt.font:                       xft:mplus Nerd Font Mono:size=11:autohint=true,\
                                  xft:Noto Color Emoji:size=9:antialias=false,\
                                  xft:Monospace:size=11:autohint=true,\
                                  xft:Unifont:size=11:autohint=true
URxvt.geometry:                   84x16
URxvt.internalBorder:             20
URxvt.cursorBlink:                true
URxvt.cursorUnderline:            true
URxvt.saveLines:                  8192
URxvt.scrollBar:                  false
URxvt.scrollBar_right:            true
URxvt.scrollBar_floating:         false
URxvt.scrollstyle:                plain
URxvt.scrollWithBuffer:           false
URxvt.urgentOnBell:               false
URxvt.depth:                      32
URxvt.iso14755:                   false
URxvt.iconFile:                   /home/username/.icons/Gladient/terminal.png

! Uncomment below if too much font spacing, and fix glyphs performance issues.
!URxvt.letterSpace:                -1
!URxvt.skipBuiltinGlyphs:          true

! Disable printing the terminal contents when pressing PrintScreen.
! The strings will be interpreted as if typed into the shell as-is.
URxvt.print-pipe:                 "cat >/dev/null"

! Clear the scrollback buffer cleanly, the shell built-in sequence replacement.
URxvt.keysym.Control-Shift-L:     command:\033c

! URxvt extensions.
URxvt.perl-ext-common:            default,matcher,resize-font,tabbedex

! Eval built-in extension.
URxvt.keysym.Control-Shift-C:     eval:selection_to_clipboard
URxvt.keysym.Control-Shift-V:     eval:paste_clipboard
URxvt.keysym.Control-Up:          eval:scroll_up 1
URxvt.keysym.Control-Down:        eval:scroll_down 1
URxvt.keysym.Control-Home:        eval:scroll_to_top
URxvt.keysym.Control-End:         eval:scroll_to_bottom

! Matcher built-in extension.
URxvt.keysym.Control-Shift-U:     matcher:select
URxvt.url-launcher:               your_web_browser
URxvt.matcher.button:             1
URxvt.matcher.rend.0:             Uline fg7

! Resize-font extension.
URxvt.keysym.Control-minus:       resize-font:smaller
URxvt.keysym.Control-plus:        resize-font:bigger
URxvt.keysym.Control-equal:       resize-font:reset
URxvt.keysym.Control-question:    resize-font:show
URxvt.resize-font.step:           1

! Tabbed-extended extension.
URxvt.tabbedex.no-tabbedex-keys:  yes
URxvt.tabbedex.new-button:        false
URXvt.tabbedex.reopen-on-close:   yes
URxvt.tabbedex.autohide:          yes
URxvt.tabbedex.tabbar-fg:         5
URxvt.tabbedex.tabbar-bg:         0
URxvt.tabbedex.tab-fg:            2
URxvt.tabbedex.tab-bg:            0
URxvt.tabbedex.bell-fg:           0
URxvt.tabbedex.bell-bg:           0
URxvt.tabbedex.bell-tab-fg:       0
URxvt.tabbedex.bell-tab-bg:       0
URxvt.tabbedex.title-fg:          7
URxvt.tabbedex.title-bg:          0
URxvt.keysym.Control-Shift-T:     tabbedex:new_tab
URxvt.keysym.Control-Shift-R:     tabbedex:rename_tab
URxvt.keysym.Control-Shift-W:     tabbedex:kill_tab
URxvt.keysym.Control-Next:        tabbedex:next_tab
URxvt.keysym.Control-Prior:       tabbedex:prev_tab
URxvt.keysym.Control-Shift-Next:  tabbedex:move_tab_right
URxvt.keysym.Control-Shift-Prior: tabbedex:move_tab_left

! Color schemes.
#define black0                    [97]#373E4D
#define black1                    #3B4252
#define black2                    #434C5E
#define black3                    #4C566A
#define red0                      #FA5AA4
#define red1                      #FA74B2
#define green0                    #2BE491
#define green1                    #44EB9F
#define yellow0                   #FA946E
#define yellow1                   #FAA687
#define blue0                     #63C5EA
#define blue1                     #7ACBEA
#define magenta0                  #CF8EF4
#define magenta1                  #D8A6F4
#define cyan0                     #89CCF7
#define cyan1                     #A1D5F7
#define white0                    [100]#F9F9F9
#define white1                    #F7F7F7
#define white2                    #F4F4F4

*.color1:                         red0
*.color2:                         green0
*.color3:                         yellow0
*.color4:                         blue0
*.color5:                         magenta0
*.color6:                         cyan0

*.color9:                         red1
*.color10:                        green1
*.color11:                        yellow1
*.color12:                        blue1
*.color13:                        magenta1
*.color14:                        cyan1

! Used by `terminal-set.sh`, do not change the following configuration.
*.foreground:                     white0
*.background:                     black0
*.cursorColor:                    white0
*.borderColor:                    black0

*.color0:                         black2
*.color7:                         white1

*.color8:                         black3
*.color15:                        white2

!*.foreground:                     black0
!*.background:                     white0
!*.cursorColor:                    black0
!*.borderColor:                    white0

!*.color0:                         white1
!*.color7:                         black2

!*.color8:                         white2
!*.color15:                        black3
```

You have to change a few settings like the part that says `username` and change it to your username. In my case it is `alex`, but after a few simple tweaks it works and works well. I love simplicity if you haven't noticed so I keep things mostly simple and clean. urxvt fits the bill usually and works quite well with my openbox configuration which uses mostly keyboard shortcuts that are configured in `rc.xml`, but that is another post for another time. but on my server and most of my headless boards I use tmux heavily

------
#### <u>tmux:</u>

Tmux is pretty neat and very useful on servers or headless computers. The reason being is you can run multiple terminals without needing as desktop environment. You can also create more windows in the session with shortcut `ctrl + b` (release after this before pressing the next key) and than press `c` with the ability to switch windows using `ctrl + b` and after releasing press `s` which is super useful when running multiple different things that shouldn't be exited once I leave the ssh session. My config is mostly the default and I really can't be bothered to modify it any further since I use it to just run programs and tasks that I don't want to run in the background via service files or whatnot so I can usually see what is going on and any errors that could be outputted to terminal or if I want a more "interactive" terminal while I'm testing things on bare metal or similar.

Tmux has many uses such as using tmux with socat to handle multiple shells using "dumb" pipes. My note for this can be found here: https://github.com/f0rg-02/Notes/blob/main/Linux/Bash/Socat%20Tmux%20Setup.md

Original post I used is: https://systemoverlord.com/2018/01/20/socat-as-a-handler-for-multiple-reverse-shells.html and is definitely a read.

The script:

```bash
#!/bin/bash

SOCKDIR=$(mktemp -d)
SOCKF=${SOCKDIR}/usock

# Start tmux, if needed
tmux start
# Create window
tmux new-window "socat UNIX-LISTEN:${SOCKF},umask=0077 STDIO"
# Wait for socket
while test ! -e ${SOCKF} ; do sleep 1 ; done
# Use socat to ship data between the unix socket and STDIO.
exec socat STDIO UNIX-CONNECT:${SOCKF}

```

Socat command:

```bash
socat OPENSSL-LISTEN:4443,cert=bind.pem,reuseaddr,verify=0,fork EXEC:./socat_tmux.sh
```

Very useful and I definitely recommend exploring what you can do.

------
#### <u>Tilix:</u>

Tilix is a somewhat different terminal. It lets you split multiple windows in one terminal window. I use this mostly on my x270 since the screen is 12.5 inches which is great for how lightweight and small it is, but this also means I don't have a lot of screen to work with so I prefer to use the screen space I do have to its best. This is where Tilix came in. I have it set as a keyboard shortcut along with my regular default terminal. This way I can use both if I want to. The reason for this is because I use Tilix mostly for when I'm testing and working on my servers, but also if I'm running a program or tools and I want to have splitted terminals so I can run multiple things and able to quickly switch and also see what is going on. This avoids having clutters of multiple terminals with multiple tabs and getting them mixed up.

Also, editing it is pretty easy since it is json files in `$HOME/.config/tilix/schemes` and pretty straight forward. I found a tokyo night theme that I like and works well with the rest of my environment.

**NOTE:Notice a theme? My eyes burn regardless, but I use gentler and darker colors to help with eye strain. I do recommend getting glasses with the blue filter to help reduce eye strain even more. I bought mine off of Zenni's Optical and I went with the more expensive, but very effective blue filter. This is a shameless promotion of Zenni's. I recommend everyone check them out and you can even get glasses without a prescription without paying $200+ for a pair.**

My config on my desktop is:

```json

{
    "name": "Tokyo Night",
    "comment": "Theme that celebrates the lights of Downtown Tokyo at night.",
    "use-theme-colors": false,
    "foreground-color": "#a9b1d6",
    "background-color": "#1a1b26",
    "palette": [
        "#1a1b26",
        "#f7768e",
        "#9ece6a",
        "#e0af68",
        "#7aa2f7",
        "#bb9af7",
        "#73daca",
        "#a9b1d6",
        "#565f89",
        "#f7768e",
        "#9ece6a",
        "#e0af68",
        "#7aa2f7",
        "#bb9af7",
        "#73daca",
        "#cfc9c2"
    ]
}
```

I did export my config from tilix after I set my layout and my keyboard shortcut is set to: `tilix -s /home/alex/.config/tilix/default_session_layout.json` 

The config pasted is:

```json

{
    "child": {
        "child1": {
            "directory": "\/home\/alex",
            "height": 687,
            "profile": "2b7c4080-0ddd-46c5-8f23-563fd3ba789d",
            "readOnly": false,
            "synchronizedInput": true,
            "type": "Terminal",
            "uuid": "d27b2f5b-7d55-4ef5-aed0-3e50d0b3e264",
            "width": 566
        },
        "child2": {
            "child1": {
                "directory": "\/home\/alex",
                "height": 343,
                "profile": "2b7c4080-0ddd-46c5-8f23-563fd3ba789d",
                "readOnly": false,
                "synchronizedInput": true,
                "type": "Terminal",
                "uuid": "9bf1f91f-3889-4572-8111-88adf7af8365",
                "width": 565
            },
            "child2": {
                "directory": "\/home\/alex",
                "height": 343,
                "profile": "2b7c4080-0ddd-46c5-8f23-563fd3ba789d",
                "readOnly": false,
                "synchronizedInput": true,
                "type": "Terminal",
                "uuid": "cc3632ff-5bf9-45f4-91de-fec8aa7cf021",
                "width": 565
            },
            "orientation": 1,
            "position": 49,
            "ratio": 0.499272197962154274,
            "type": "Paned"
        },
        "orientation": 0,
        "position": 50,
        "ratio": 0.5,
        "type": "Paned"
    },
    "height": 687,
    "name": "${title}",
    "synchronizedInput": false,
    "type": "Session",
    "uuid": "e1fa2f38-5aff-4a98-af4f-9e56099048bb",
    "version": "1.0",
    "width": 1132
}
```

------

#### <u>A tweak: ohmyphosh </u>

I mentioned ohmyphosh briefly earlier and I have to say, it makes my terminal look cooler and for the most part is pretty useless for me or I think I just don't use it as intended, but I do like it. The [homepage](https://ohmyposh.dev/) describes it as "a prompt theme engine for any shell" which is on point, but also can be pretty useful to a certain point. Install is pretty easy and I use the "manual" installation for Linux: https://ohmyposh.dev/docs/installation/linux 

which is just a curl command and piping to run with bash. I should note it does require running as root/sudo and I'm a stickler to avoiding switching to root as much as possible so the command I use is slightly modified: `curl -s https://ohmyposh.dev/install.sh | sudo bash -s`

The script pasted:

```bash
#!/usr/bin/env sh

install_dir=""
themes_dir=""
executable=""

error() {
    printf "\x1b[31m$1\e[0m\n"
    exit 1
}

info() {
    printf "$1\n"
}

warn() {
    printf "⚠️  \x1b[33m$1\e[0m\n"
}

help() {
    # Display Help
    echo "Install script for Oh My Posh"
    echo
    echo "Syntax: install.sh [-h|d|t]"
    echo "\noptions:"
    echo "-h     Print this help."
    echo "-d     Specify the installation directory. Defaults to /usr/local/bin or the directory where oh-my-posh is installed."
    echo "-t     Specify the themes installation directory. Defaults to the oh-my-posh cache directory."
    echo
}

while getopts ":hd:t:" option; do
   case $option in
      h) # display Help
         help
         exit;;
      d) # Enter a name
         install_dir=${OPTARG};;
      t) # themes directory
         themes_dir=${OPTARG};;
     \?) # Invalid option
         echo "Invalid option command line option. Use -h for help."
         exit 1
   esac
done

SUPPORTED_TARGETS="linux-386 linux-amd64 linux-arm linux-arm64 darwin-amd64 darwin-arm64 freebsd-386 freebsd-amd64 freebsd-arm freebsd-arm64"

validate_dependency() {
    if ! command -v $1 >/dev/null; then
        error "$1 is required to install Oh My Posh. Please install $1 and try again.\n"
    fi
}

validate_dependencies() {
    validate_dependency curl
    validate_dependency unzip
    validate_dependency realpath
    validate_dependency dirname
}

set_install_directory() {
    if [ -n "$install_dir" ]; then
        # expand directory
        install_dir="${install_dir/#\~/$HOME}"
        return 0
    fi

    # check if we have oh-my-posh installed, if so, use the executable directory
    # to install into and follow symlinks
    if command -v oh-my-posh >/dev/null; then
        posh_dir=$(command -v oh-my-posh)
        real_dir=$(realpath $posh_dir)
        install_dir=$(dirname $real_dir)
        info "Oh My Posh is already installed, updating existing installation in:"
        info "  ${install_dir}"
    else
        install_dir="/usr/local/bin"
    fi
}

validate_install_directory() {
    if [ ! -d "$install_dir" ]; then
        error "Directory ${install_dir} does not exist, set a different directory and try again."
    fi

    # check if we can write to the install directory
    if [ ! -w $install_dir ]; then
        error "Cannot write to ${install_dir}. Please set a different directory and try again: \n  curl -s https://ohmyposh.dev/install.sh | bash -s -- -d {directory}"
    fi

    # check if the directory is in the PATH
    good=$(
        IFS=:
        for path in $PATH; do
        if [ "${path%/}" = "${install_dir}" ]; then
            printf 1
            break
        fi
        done
    )

    if [ "${good}" != "1" ]; then
        warn "Installation directory ${install_dir} is not in your \$PATH"
    fi
}

validate_themes_directory() {
    if [ ! -d "$install_dir" ]; then
        error "Directory ${install_dir} does not exist, set a different directory and try again."
    fi

    # check if we can write to the install directory
    if [ ! -w $install_dir ]; then
        error "Cannot write to ${install_dir}. Please set a different directory and try again: \n  curl -s https://ohmyposh.dev/install.sh | bash -s -- -d {directory}"
    fi

    # check if the directory is in the PATH
    good=$(
        IFS=:
        for path in $PATH; do
        if [ "${path%/}" = "${install_dir}" ]; then
            printf 1
            break
        fi
        done
    )

    if [ "${good}" != "1" ]; then
        warn "Installation directory ${install_dir} is not in your \$PATH"
    fi
}

install_themes() {
    if [ -n "$themes_dir" ]; then
        # expand directory
        themes_dir="${themes_dir/#\~/$HOME}"
    fi

    cache_dir=$($executable cache path)

    # validate if the user set the path to the themes directory
    if [ -z "$themes_dir" ]; then
        themes_dir="${cache_dir}/themes"
    fi

    # Validate if the themes directory exists
    if [ ! -d "$themes_dir" ]; then
        mkdir -p $themes_dir
    fi

    info "🎨 Installing oh-my-posh themes in ${themes_dir}\n"

    zip_file="${cache_dir}/themes.zip"

    url="https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip"

    http_response=$(curl -s -f -L $url -o $zip_file -w "%{http_code}")

    if [ $http_response == "200" ] && [ -f $zip_file ]; then
        unzip -o -q $zip_file -d $themes_dir
        # make sure the files are readable and writable for all users
        chmod a+rwX ${themes_dir}/*.omp.*
        rm $zip_file
    else
        warn "Unable to download themes at ${url}\nPlease validate your curl, connection and/or proxy settings"
    fi
}

install() {
    arch=$(detect_arch)
    platform=$(detect_platform)
    target="${platform}-${arch}"

    good=$(
        IFS=" "
        for t in $SUPPORTED_TARGETS; do
        if [ "${t}" = "${target}" ]; then
            printf 1
            break
        fi
        done
    )

    if [ "${good}" != "1" ]; then
        error "${arch} builds for ${platform} are not available for Oh My Posh"
    fi

    info "\nℹ️  Installing oh-my-posh for ${target} in ${install_dir}"

    executable=${install_dir}/oh-my-posh
    url=https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-${target}

    info "⬇️  Downloading oh-my-posh from ${url}"

    http_response=$(curl -s -f -L $url -o $executable -w "%{http_code}")

    if [ $http_response != "200" ] || [ ! -f $executable ]; then
        error "Unable to download executable at ${url}\nPlease validate your curl, connection and/or proxy settings"
    fi

    chmod +x $executable

    install_themes

    info "🚀 Installation complete.\n\nYou can follow the instructions at https://ohmyposh.dev/docs/installation/prompt"
    info "to setup your shell to use oh-my-posh."
    if [ $http_response == "200" ]; then
        info "\nIf you want to use a built-in theme, you can find them in the ${theme_dir} directory:"
        info "  oh-my-posh init {shell} --config ${theme_dir}/{theme}.omp.json\n"
    fi
}

detect_arch() {
  arch="$(uname -m | tr '[:upper:]' '[:lower:]')"

  case "${arch}" in
    x86_64) arch="amd64" ;;
    armv*) arch="arm" ;;
    arm64) arch="arm64" ;;
    aarch64) arch="arm64" ;;
    i686) arch="386" ;;
  esac

  if [ "${arch}" = "arm64" ] && [ "$(getconf LONG_BIT)" -eq 32 ]; then
    arch=arm
  fi

  printf '%s' "${arch}"
}


detect_platform() {
  platform="$(uname -s | awk '{print tolower($0)}')"

  case "${platform}" in
    linux) platform="linux" ;;
    darwin) platform="darwin" ;;
  esac

  printf '%s' "${platform}"
}

validate_dependencies
set_install_directory
validate_install_directory
install
```

------

I have the clean detailed configured on my laptop and desktop which is simple, nice, and does give useful information when I do look at the ohmyphosh prompt.

The clean detailed theme: https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/clean-detailed.omp.json

And the paste: 

```json
{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "blocks": [
    {
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "background": "#FEF5ED",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "properties": {
            "macos": "\uf179 ",
            "ubuntu": "\uf31b ",
            "windows": "\ue62a "
          },
          "style": "diamond",
          "template": " {{ if .WSL }}WSL at {{ end }}{{.Icon}}",
          "trailing_diamond": "<transparent,#FEF5ED>\ue0b2</>",
          "type": "os"
        },
        {
          "background": "#FEF5ED",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "style": "diamond",
          "template": "\uf489 {{ .Name }}",
          "trailing_diamond": "<transparent,#FEF5ED>\ue0b2</>",
          "type": "shell"
        },
        {
          "background": "#516BEB",
          "foreground": "#ffffff",
          "leading_diamond": "\ue0b2",
          "style": "diamond",
          "template": "\ue266 MEM: {{ round .PhysicalPercentUsed .Precision }}% | {{ (div ((sub .PhysicalTotalMemory .PhysicalAvailableMemory)|float64) 1073741824.0) }}/{{ (div .PhysicalTotalMemory 1073741824.0) }}GB \ue266 ",
          "trailing_diamond": "<transparent,#516BEB>\ue0b2</>",
          "type": "sysinfo"
        },
        {
          "background": "#575656",
          "foreground": "#d6deeb",
          "leading_diamond": "\ue0b2",
          "properties": {
            "style": "roundrock",
            "threshold": 0
          },
          "style": "diamond",
          "template": " {{ .FormattedMs }} ",
          "trailing_diamond": "\ue0b0",
          "type": "executiontime"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "right",
      "segments": [
        {
          "background": "#17D7A0",
          "foreground": "#011627",
          "leading_diamond": "\ue0b2",
          "properties": {
            "branch_icon": "\ue725 ",
            "fetch_stash_count": true,
            "fetch_status": true,
            "fetch_upstream_icon": true,
            "fetch_worktree_count": true
          },
          "style": "diamond",
          "template": " {{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \ueb4b {{ .StashCount }}{{ end }} ",
          "trailing_diamond": "\ue0b0",
          "type": "git"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "style": "plain",
          "template": "\u256d\u2500",
          "type": "text"
        },
        {
          "properties": {
            "time_format": "15:04"
          },
          "style": "plain",
          "template": " \u2665 {{ .CurrentDate | date .Format }} |",
          "type": "time"
        },
        {
          "style": "plain",
          "template": " \uf292 ",
          "type": "root"
        },
        {
          "properties": {
            "folder_icon": "\uf07b ",
            "folder_separator_icon": " \uf061 ",
            "home_icon": "\ueb06 "
          },
          "style": "plain",
          "template": " {{ .Path }} ",
          "type": "path"
        }
      ],
      "type": "prompt"
    },
    {
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "properties": {
            "always_enabled": true
          },
          "style": "plain",
          "template": "\u2570\u2500 ",
          "type": "status"
        }
      ],
      "type": "prompt"
    }
  ],
  "console_title_template": "{{ .Folder }}",
  "transient_prompt": {
    "background": "transparent",
    "foreground": "#FEF5ED",
    "template": "\ue285 "
  },
  "version": 2
}
```

And to run it on every prompt that is opened I added this to my `.bashrc` :

```bash
eval "$(oh-my-posh init bash --config /home/alex/.config/ohmyphosh/themes/clean-detailed.omp.json)"

```

For my server to help distinguish between that prompt and my host computer's prompt when I'm connected to it via ssh I use the gruvbox theme. That can be found here: https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/gruvbox.omp.json

And the paste: 

```json
{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "blocks": [
    {
      "alignment": "left",
      "segments": [
        {
          "background": "#3A3A3A",
          "foreground": "#ffffff",
          "style": "powerline",
          "template": "{{ if .WSL }}WSL at{{ end }} {{.Icon}} ",
          "type": "os"
        },
        {
          "background": "#458588",
          "foreground": "#282828",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "style": "full"
          },
          "style": "powerline",
          "template": " {{ .Path }} ",
          "type": "path"
        },
        {
          "background": "#98971A",
          "background_templates": [
            "{{ if or (.Working.Changed) (.Staging.Changed) }}#FF9248{{ end }}",
            "{{ if and (gt .Ahead 0) (gt .Behind 0) }}#ff4500{{ end }}",
            "{{ if gt .Ahead 0 }}#B388FF{{ end }}",
            "{{ if gt .Behind 0 }}#B388FF{{ end }}"
          ],
          "foreground": "#282828",
          "leading_diamond": "\ue0b6",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "branch_max_length": 25,
            "fetch_stash_count": true,
            "fetch_status": true,
            "branch_icon": "\uE0A0 ",
            "branch_identical_icon": "\u25CF"
          },
          "style": "powerline",
          "template": " {{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \ueb4b {{ .StashCount }}{{ end }} ",
          "trailing_diamond": "\ue0b4",
          "type": "git"
        },
        {
          "background": "#8ED1F7",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "fetch_version": true
          },
          "style": "powerline",
          "template": " \ue626 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "type": "go"
        },
        {
          "background": "#4063D8",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "fetch_version": true
          },
          "style": "powerline",
          "template": " \ue624 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "type": "julia"
        },
        {
          "background": "#FFDE57",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "display_mode": "files",
            "fetch_virtual_env": false
          },
          "style": "powerline",
          "template": " \ue235 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "type": "python"
        },
        {
          "background": "#AE1401",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "display_mode": "files",
            "fetch_version": true
          },
          "style": "powerline",
          "template": " \ue791 {{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "type": "ruby"
        },
        {
          "background": "#FEAC19",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "display_mode": "files",
            "fetch_version": false
          },
          "style": "powerline",
          "template": " \uf0e7{{ if .Error }}{{ .Error }}{{ else }}{{ .Full }}{{ end }} ",
          "type": "azfunc"
        },
        {
          "background_templates": [
            "{{if contains \"default\" .Profile}}#FFA400{{end}}",
            "{{if contains \"jan\" .Profile}}#f1184c{{end}}"
          ],
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "display_default": false
          },
          "style": "powerline",
          "template": " \ue7ad {{ .Profile }}{{ if .Region }}@{{ .Region }}{{ end }} ",
          "type": "aws"
        },
        {
          "background": "#ffff66",
          "foreground": "#111111",
          "powerline_symbol": "\ue0b0",
          "style": "powerline",
          "template": " \uf0ad ",
          "type": "root"
        }
      ],
      "type": "prompt"
    }
  ],
  "console_title_template": "{{ .Folder }}",
  "final_space": true,
  "version": 2
}
```

For the `.bashrc` I've added:

```bash
eval "$(oh-my-posh init bash --config /home/alex/.config/ohmyphosh/themes/gruvbox.omp.json)"
```

Simple, right? I have a lot more configurations that I've done in terminals alone, but unfortunately this is already obnoxiously long and I'm bored. 

------
### <u>Brief final thoughts:</u>

See simplicity is beautiful and the limit is near limitless with proper documentation and enough caffeine. Most programs, tools, utils, applications, etc are made to be used and understood very simply but people for some reason over complicate everything. Why? I have no idea. Doesn't make anyone seem or look smarter. It makes them look like a pseudo-intellect and stupid to me. Sure a bit harsh, but I'm not going to sugar coat anything and I'm also honest. What works for me might not work for you and figuring out what does work for you is really interesting and definitely rewarding if you take the time to try new things and get out of your comfort zone.