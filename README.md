##NSpec code katas without Visual Studio

This is a [WarmuP](https://github.com/chucknorris/warmup) template for doing code katas using NSpec **(it can be used as a base template for doing any kind of .Net development in VIM, actually)**. This readme also contains instructions for using VIM for these code katas.  Its purpose is to really put an emphasis on the kata and test driven development in a lean development environment.  After you get the hang of it, you may find that you're as productive in vim when compared to Visual Studio.

##Why would you want to do .Net dev outside of Visual Studio?

Visual Studio doesn't provide the plugins I need for web development in a timely manner. Plugins such as coffeescript convertion and syntax highlighting, zen coding, git integration, jslint, etc just lag behind (some of these plugins take many months to make it over to Visual Studio). As of this point, Visual Studio plugin authors simply can't keep up to the "not .Net" development ecosystem. Also (for example), there is a **competitive advantage** that you get when you can use coffeescript **a year** before Visual Studio gains that capability. Same goes for scss/sass integration and zen coding...I don't want to wait to for Visual Studio to catch up to use these incredibly productive tools (yes, coffeescript, scss/sass plugins exist now...finally...but too little too late).

Here is a short list of things that vim gives you (and takes away). Feel free to send me a pull request if you come up with any others:

The good

- full customization of the text editor, a means to create plugins that can be applied to development outside of .Net
- fast startup and runtime
- **faster access to plugins specific to other languages (css, javascript, html, go, clojure, haskell, elixir, ruby...the list goes on)**
- free (and unrestricted)
- better window management and file navigation
- stupid fast "general" text manipulation
- can be used for development outside of .Net, across OS'es and languages
- you'll be "that bad ass mofo" that uses vim and code circles around everyone else (yes, getting proficient with vim key bindings will make you that good)
- a good vim story will bring developers from other stacks to try .Net development
- your build, test, and general SDLC will revolve around the command line, positioning yourself for automation of "all things" (IDE independent)
- better autocompletion for non-C# words and your own C# code
- **yes, you still get autocompletion for the .Net framework (though arguably not as good)**

The bad

- steep learning curve (2-3 month commitment, but well worth it)
- **I've included a vim tutorial for you to practice. Copy the following text into vim and work through it: [vim tutorial](https://raw.github.com/amirrajan/katanspec/master/vim_tutorial.txt)**
- no built-in debugger (it's a text editor not an IDE, heavy emphasis on testing and Console.WriteLine). If you need to debug, you can install an Express Edition of Visual Studio and insert the following line of code anywhere in your app to initiate debugging: `System.Diagnostics.Debugger.Launch()`
- heavy use of the command line
- .Net's project and solution files make it a painful to change files (rake and WarmuP help solve this)
- you're starting from scratch, stitching together your vim environment (especially for .Net development)
- yes, you still get autocompletion for the .Net framework (though arguably not as good)
- no Resharper
- you'll be "that guy/gal that uses vim for everything"
- you may lose childhood memories as you become more proficient with vim trying remember all the shortcut's you've created
- until this process is fully baked, you may have to "visit the mothership" to do more complex project and solution manipulations

##Vim Tutorial
You can take [this file](https://github.com/amirrajan/katanspec/blob/master/vim_tutorial.txt) and copy and paste it into VIM, work through it for a nice kickstart!

##Getting your "dev" environment setup on Windows

The setup is still pretty manual. As this evolves, ideally there will be a chocolatey package that will get your entire environment up and running. For now this read me will have to do...

**You have to run your command line as an admin for this entire setup.**

- install [chocolatey](http://chocolatey.org/)

It's apt-get for Windows.

- install [git for windows](http://git-scm.com/download/win)

This is what will add vim to your system.  Keep in mind that this is vim and not gVim.

- install gVim via chocolatey by running: `cinst vim`

This will be used to bootstrap .net solutions and give you access to a powerful programming language called ruby

- install ruby via chocolatey by running: `cinst ruby`
- install ruby devkit (gives you the ability to natively compile gems) via chocolatey by running: `cinst ruby.devkit`

Be sure to add ruby to your PATH (you may have to restart Windows for path updates to take affect), ruby is used for rake (build automation), warmup (solution/project generation) and nokogiri (xml file/csproj manipulation)

- install ctags via chocolatey by running: `cinst ctags`

Ctags is used for auto completion and "go to definition" in vim.

- install ctags via chocolatey by running: `cinst growl`

This will give you notifications of when builds and tests fail. Open up Growl once so that the C:\Users\%USER%\AppData\Local\Growl\2.0.0.0\Displays\ directory gets created, then...

- install [Translucent Dark](http://softwarebakery.com/frozencow/translucentdark.html), extract the theme to C:\Users\%USER%\AppData\Local\Growl\2.0.0.0\Displays\TranslucentDark

This is a really nice theme for Growl for Windows. [Here are the settings I use](http://i.imgur.com/buWyf.png).

- install conemu via chocolatey by running: `cinst conemu`

This is an incredibly awesome tabbed and split console window manager. We'll customize everything in the next section.

- install perl via chocolatey by running: `cinst strawberryperl`

This is needed to for a package called ack (and of course opens you up to using packages built in perl). Ack provides a very nice way to search for text in a directory.

- install ack via chocolatey by running: `cinst ack`

This will install ack, a powerful perl based text search tool

##Installing packages

**You have to run your command line as an admin for this entire setup.**

- from the command line run: `gem install warmup`

This will install a templating engine used to create .Net solutions

- from the command line run: `gem install nokogiri`

This will install an xml manipulation library used to mainpulate project and solution files

- download [pathogen](https://github.com/tpope/vim-pathogen) as a zip, then extract the files and copy the autoload folder to `C:\Program Files (x86)\vim\vim73`

Pathogen is a way to manage vim plugins without polluting the install directory

##Making ConEmu pretty and functional

- set up your fonts

<a href="http://imgur.com/ajrC3Bt"><img src="http://i.imgur.com/ajrC3Bt.png" title="Hosted by imgur.com"/></a>

- set up your colors

<a href="http://imgur.com/DKipf0h"><img src="http://i.imgur.com/DKipf0h.png" title="Hosted by imgur.com"/></a>

- create a startup script

<a href="http://imgur.com/TTU0pQH"><img src="http://i.imgur.com/TTU0pQH.png" title="Hosted by imgur.com"/></a>

with the following text

<pre>
C:\Windows\System32\cmd.exe -cur_console:as75H -new_console:d:{YOURSTARTUPDIRECTORY}

C:\Windows\System32\cmd.exe -cur_console:as25H  -new_console:d:{YOURSTARTUPDIRECTORY}
</pre>

- and then add set the script to run at startup

<a href="http://imgur.com/29PxiNP"><img src="http://i.imgur.com/29PxiNP.png" title="Hosted by imgur.com"/></a>

- change this key binding from Ctrl + V to Shift + Ctrl + V

You'll still use Ctrl + V to paste in vim, but use Shift + Ctrl + V to paste in the rest of ConEmu

<a href="http://imgur.com/aZlRVzH"><img src="http://i.imgur.com/aZlRVzH.png" title="Hosted by imgur.com"/></a>

##Installing vim plugins

- set up your vimrc (Here is what mine looks like, you can customize yours more specifially later). To get the location for your vimrc file, refer to [this StackOverflow answer](http://stackoverflow.com/questions/8977649/how-to-locate-the-vimrc-file-used-by-vim-editor), the default location should be `C:\Users\USERNAME\_vimrc` (no extension) (you can create one here if it doesn't exist).

**[Copy the contents of this file into your vimrc](https://raw.github.com/amirrajan/katanspec/master/samplevimrc.txt)**

With pathogen, all vim plugins can be installed by cloning git repositories. The default location for plugin installations are `C:\Users\%USER%\vimfiles\bundle`. So navigate to that directory and you can run `git clone PATHTOGITREPO` to install plugins.

- Nerd tree: `git clone https://github.com/scrooloose/nerdtree.git`

This will give you a file explorer in vim. You'll see it to the left when vim loads.

- CtrlP: `git clone https://github.com/kien/ctrlp.vim.git`

This will give you quick file navigation. Press `ctrl+p` and you'll git a file listing that can be searched. Press `enter` to open file, `ctrl+v` to open file in a vertical split and `ctrl+x` to open the file in a horizontal split.

- Ack: `git clone https://github.com/mileszs/ack.vim.git`

This will give you text search in Vim. In command mode type `:Ack` to search for all instances of a word under the cursor or `:Ack SEARCHTERM` for all instances of words you specifiy.

- Ctags is already integrated, you can use `ctrl+]` to go to definition. [Here are some more keyboard shortcuts](http://stackoverflow.com/questions/563616/vim-and-ctags-tips-and-tricks)

- supertab: `git clone https://github.com/ervandew/supertab.git`

This will give you auto completion by pressing `TAB`, you can still use `ctrl+n` to autocomplete (all integrate with ctags).

- vim-csharp: `git clone https://github.com/OrangeT/vim-csharp.git`

Sytnax highlighting for csharp and razor

- vim-easymotion `git clone https://github.com/Lokaltog/vim-easymotion.git`

This will give you quick jump capabilities in vim. Press the `leader key` twice and then a `motion key`, for example (given your leader key is mapped to ','): `,,j` will give you a jump index for all lines going down.

- zencoding `git clone https://github.com/mattn/zencoding-vim.git`

Fast html creation. More info and demo on website.

- Omnisharp. `git clone https://github.com/nosami/Omnisharp.git`

Intellesence for VIM (the vimrc provided above in this set of instructions **will** work with Omnisharp, you just need to install the plugin). Go here for install instructions https://github.com/nosami/Omnisharp

- unstack `git clone https://github.com/mattboehm/vim-unstack`

SpecWatchr (a nuget package included with this template), will write out test failures to a `stacktrace.txt` file. You can open this file, highlight lines and press `<leader>s`, (if you used the vimrc from here, your `<leader>` key is `,`). After entering that command the files associated with the stacktrace will be opened.  For more information about [unstack, visit the github page](https://github.com/mattboehm/vim-unstack).

- Snipmate and friends:
  - `git clone https://github.com/tomtom/tlib_vim.git`
  - `git clone https://github.com/MarcWeber/vim-addon-mw-utils.git`
  - `git clone https://github.com/garbas/vim-snipmate.git`

Snipmate will give you code templates. To use: 

- clone the git repositories above into your pathogen directory
- then go to the `vim-snipmate\` directory and add a `snippets` folder
- add a `snippets` folder
- under the `vim-snipmate\snippets` folder add a file called `cs.snippets` (the pattern is `filename`.snippets. other examples: `js.snippets` `html.snippets`)
- open `cs.snippets` in a text editor and paste the following text into it:

<pre>
snippet if
        if (${1}) 
        {
            ${0}
        }
</pre>

- now, when you open a `cs` file, typing `if<tab>` will expand to the block above.
- for more snippets goto: https://github.com/honza/vim-snippets/tree/master/snippets

##DONE! Now to start a kata

Once you've set up your environment. Here is how you start a code kata in Vim.

- start Growl for Windows
- open ConEmu
- navigate to a directory where you keep your katas
- run the command `warmup http://github.com/amirrajan/katanspec YOURKATANAME`
- type `vim` (for the console version) or `gvim` (for the windowed version)
- create a git repo by entering `command` mode and typing `!git init`
- and create your first commit by entering `command` mode and typing `!git add -A`
- and then `!git commit -m "first commit"`
- in the ConEmu window to the top right, navigate to the newly created directory and run `sidekick.bat`
- add a class via vim by entering `command` mode and typing `!rake add_class[Person]`
- add code as you usually would, `sidekick (aka specwatchr)` will build the application, run ctags, and run tests for you
- add a test class by via vim by entering `command` mode and typing `!rake add_test[describe_Person]`
- write a failing test using [NSpec](http://nspec.org) and see `sidekick (aka specwatchr)` run the test for you
- if you have a large amount of compiler errors, you can type `:make` in `command` mode, which will take you to the first compiler error, typing `:cw` will give you a list of all compiler errors that you can traverse through
