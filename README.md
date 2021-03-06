My Aliases
==========
My Linux config files, three handy text files, and an install script to put them all in a right place.
There is also a [website] (http://gto76.github.io/my-aliases/index.html) generated from the text files.

Quick overview
--------------

```
.
├── dotfiles
│   ├── .nrss
│   │   └── config - Few rss feeds.
│   ├── .my_bash_aliases - My aliases and functions. Can be used alone.
│   ├── .my_bashrc - Aliases that only work with other files in a project.
│   ├── .my_bashrc_personal - Few aliases that are locale specific.
│   ├── .my_vimrc - My vim configuration.
│   ├── .Xmodmapus - Keymap. 'jikl' become arrow keys when capslock is pressed.
│   └── .Xmodmapusvi - Same, but with 'hjkl' for arrows.
│   ├── .Xmodmapsi - Slovenian version of .Xmodmapus.
│   ├── .Xmodmapsivi - Same, but with 'hjkl' for arrows.
├── keymaps
│   └── Reaper Shortcuts Jure 04.ReaperKeyMap - My Reaper DAW keymap.
├── textfiles
│   ├── INS - List of things I first set up on a fresh install.
│   ├── NYK - Summaries of interesting computer topics.
│   └── WTF-MAN - Long list of Unix commands.
├── install - Links dotfiles to HOME and textfiles to Desktop.
└── README.md - You are here.
```

Two biggest and most important files are:

* [**`./dotfiles/.my_bash_aliases`**](dotfiles/.my_bash_aliases) and 
* [**`./textfiles/WTF-MAN`**](textfiles/WTF-MAN). 
    

The first one contains handy bash functions and aliases. It can be used without other files in a project; just copy it in home directory and add this line: `. ~/.my_bash_aliases` to `.bashrc` (which is also located in home directory, if not create it). If you want to use the whole project then instead use install script (see below).

Other big file [**`WTF-MAN`**](textfiles/WTF-MAN), contains short explanations and examples of useful Unix commands. 

Once everything is installed, they are easily accessible with the following commands: 
* **`m1`** - `'less WTF-MAN'`
* **`m2`** - `'less .bash_alisases'`
* **`v1`** - `'vim WTF-MAN'`
* **`v2`** - `'vim .bash_aliases'`
* **`n1`** - `'nano WTF-MAN'`
* **`n2`** - `'nano .bash_aliases'`

Also note that if you change anything in [**`.my_bash_aliases`**](dotfiles/.my_bash_aliases), you need to restart bash with `bash` command, or its `ba` alias.

How to install
--------------

```bash
cd
git clone https://github.com/gto76/my-aliases.git
cd my-aliases
./install
bash
```

Files in detail
---------------

### [`install`](install)
Executable bash script that creates symbolic links to all dot and text files of the project and places them in home and Desktop directory. If file with same name already exists, it is not overwritten, only a warning gets printed. At the end following lines are added to the `.bashrc` file in your home directory:
``` bash
if [ -f ~/.my_bashrc ]; then
   . ~/.my_bashrc
fi
```
This way aliases and functions in [**`.my_bashrc`**](dotfiles/.my_bashrc) get loaded at terminal startup. [**`.my_bashrc`**](dotfiles/.my_bashrc) then loads other two files ([**`.my_bash_aliases`**](dotfiles/.my_bash_aliases) and [**`.my_bashrc_personal`**](dotfiles/.my_bashrc_personal)) in a same manner.
Also following line: `so ~/.my_vimrc` is added to the end of a `.vimrc` file, which loads [**`.my_vimrc`**](dotfiles/.my_vimrc) at vim startup. 

To execute it run:
```
    ./install
```
Of course you can also create links yourself, or even just copy the files if you don't intend to commit changes.

### [**`.my_bashrc`**](dotfiles/.my_bashrc)
Includes aliases and functions that need other files from the project to function. In detail:
* Loads aliases and functions from [**`.my_bash_aliases`**](dotfiles/.my_bash_aliases) and [**`.my_bashrc_personal`**](dotfiles/.my_bashrc_personal).

* Exports path of [**`WTF-MAN`**](textfiles/WTF-MAN) and [**`INS`**](textfiles/INS) files. That are set to `$HOME/Desktop/WTF-MAN` and `$HOME/Desktop/INS`.

* Defines aliases **`us`**, **`usvi`**, **`si`** and **`sivi`**, that set up my custom keymaps defined in [**`.Xmodmapus`**](dotfiles/.Xmodmapus), [**`.Xmodmapusvi`**](dotfiles/.Xmodmapusvi), [**`.Xmodmapsi`**](dotfiles/.Xmodmapsi) and [**`.Xmodmapsivi`**](dotfiles/.Xmodmapsivi) (see below for details).

* Defines aliases that enable easy access to [**`.my_bash_aliases`**](dotfiles/.my_bash_aliases) `(2)`, [**`WTF-MAN`**](textfiles/WTF-MAN) `(1)`, [**`INS`**](textfiles/INS) `(4)` and to itself [**`.my_bashrc`**](dotfiles/.my_bashrc) `(3)`. They are composed out of a letter and a number. Letter signifies a program (m - less, v - vim, n - nano, g - gedit) and number a file. So for example alias **`g4`** opens [**`INS`**](textfiles/INS) with gedit.

### [`.my_bash_aliases`](dotfiles/.my_bash_aliases)
My own `.bash_aliases`. Besides a lot of useful aliases, there are also some interesting functions, such as:

* **`teaceroute1`** - Prints country codes of hosts on path.

* **`www`** - Traceroutes one server per country, prints country codes of hosts on path. 

* **`spilej`** - Plays an artist/song/album. First looks in pwd, then runs locate to search whole file system. At the end it tries to find it on YouTube and download the video and convert it to audio and play it. Most of the problems occur at search phase.

* **`catOrLess`** - Runs either cat or less, depending on size of output. Works with files or input stream.

* **`weathr`** - Weather report. Needs city ID -> Go to yahoo weather, search your location, and copy its id from address bar.

* **`noh`** - How many people are on network beside you (number of hosts).

* **`ip1`** - What's my internal ip.

* **`ip2`** - What's my external ip.

* **`pingAll`** - Pings gateway, 8.23.224.10 (website of no-ip) and Google.

* **`gi`** - Downloads small image of a phrase from Google images.

* **`wi`** - Tries to find description of a command using `whatis`, `apt-cache show` and `type`. Returns first match.

### [`WTF-MAN`](textfiles/WTF-MAN)
Long list of Unix commands with short descriptions. Useful for quick search before you start googling. In [**`.my_bashrc`**](dotfiles/.my_bashrc) there are a few aliases that enable quick access, namely:
* **`m1`** - `'less ~/Desktop/WTF-MAN'`
* **`c1`** - `'grep ~/Desktop/WTF-MAN'`
* **`v1`** - `'vim ~/Desktop/WTF-MAN'`
* **`n1`** - `'nano ~/Desktop/WTF-MAN'`

### [**`.Xmodmapus`**](dotfiles/.Xmodmapus), [**`.Xmodmapusvi`**](dotfiles/.Xmodmapusvi), [**`.Xmodmapsi`**](dotfiles/.Xmodmapsi) and [**`.Xmodmapsivi`**](dotfiles/.Xmodmapsivi)
Keymaps that make CapsLock an additional modifier key. With it pressed, the keys under your right arm become numpad keys (the ones with NumLock off, e.g. Arrows, Home, End, PgUp...), but with few additions like: 'k' key that corresponds to '5' on a numpad becomes down key, 'p' becomes backspace, ';' enter, '/' delete, and "'" escape. Also space becomes enter, backspace delete, '`' escape, all the number keys their corresponding F keys and Insert key becomes CapsLock. There is also a Vi variation, which has directional keys positioned in Vi style and Home, End, PgUp, PgDn keys a little shifted around. Here are the two American versions:
- **.Xmodmapus**

![Alt text](/doc/Xmodmapus.png?raw=true "Picture of Keyboard")

- **.Xmodmapusvi**

![Alt text](/doc/Xmodmapusvi.png?raw=true "Picture of Keyboard")

Also present are Slovenian versions: [**`.Xmodmapsi`**](dotfiles/.Xmodmapsi) and [**`.Xmodmapsivi`**](dotfiles/.Xmodmapsivi). Slovenian layout is basically the same as German with letters 'čćšđž' in place of 'umlauted' letters. 

How to set keymap
-----------------

Warning: For keymaps to work, it is mandatory that layout for that language is set before `xmodmap` is run. For example if American layout is selected and we want Slovenian we need to type:
```
	setxkbmap -layout si
	xmodmap ~/.Xmodmapsi
```
In [**`.my_bashrc`**](dotfiles/.my_bashrc) there are aliases that do this for you:
* **`us`** - American layout,
* **`usvi`** - vi variation of American layout,
* **`si`** - Slovenian layout and
* **`sivi`** - vi variation of Slovenian layout.

If you want a particular keymap to get loaded when X starts (at least for Mint/Debian), go to Startup Applications and add new application: `xmodmap $HOME/.Xmodmapus` with 2 second delay.

### Reaper Shortcuts Jure 04.ReaperKeyMap
Custom shortcuts for Reaper DAW (digital audio workstation).

![Alt text](/doc/reaper-keyboard-shortcuts.png?raw=true "Picture of Keyboard")
Mind that there are a lot of other shortcuts not on picture, that use modifiers.


