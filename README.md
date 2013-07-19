##NSpec code katas without Visual Studio

This is a WarmuP template for doing code katas using NSpec. This readme also contains instructions for using VIM for these code katas.  It's purpose is to really put an emphasis on the kata and test driven development in a lean development environment.  After you get the hang of it, you may find that you're as productive in vim when compared to Visual Studio.

##Why would you want to do .Net dev outside of Visual Studio?

Visual Studio doesn't provide the plugins I need for web development in a timely manner. Plugins such as coffeescript convertion and syntax highlighting, zen coding, git integration, jslint, etc just lag behind (some of these plugins take many months to make it over to Visual Studio). As of this point, Visual Studio plugin authors simply can't keep up to the "not .Net" development ecosystem. Also (for example), there is a **competitive advantage** that you get when you can use coffeescript **a year** before Visual Studio gains that capability. Same goes for scss/sass integration and zen coding...I don't want to wait to for Visual Studio to catch up to use these incredibly productive tools (yes, coffeescript, scss/sass plugins exist now...finally...but too little too late).

Here is a short list of things that vim gives you (and takes away). Feel free to send me a pull request if you come up with any others:

The good

- full customization of the text editor, a means to create plugins that can be applied to development outside of .Net
- fast startup and runtime
- faster access to plugins
- free
- better window management and file navigation
- stupid fast text manipulation
- can be used for development outside of .Net, across OS'es and languages
- you'll be "that bad ass mofo" that uses vim and code circles around everyone else (yes, getting proficient with vim key bindings will make you that good)
- a good vim story will bring developers from other stacks to try .Net development
- you're build, test, and general SDLC will revolve around the command line, positioning yourself for automation of "all things"

The bad

- steep, steep learning curve (2-3 month commitment, but well worth it)
- no built in debugger (it's a text editor not an IDE, heavy emphasis on testing and Console.WriteLine)
- heavy use of the command line
- .Net's project and solution files make it a painful to change files (rake solves this)
- you're starting from scratch, stitching together your vim environment (especially for .Net development)
- poor autocompletiong for .Net BCL (not your own classes however)
- refactoring can be a pain (on the plus side, you'll find that your api's are more consistent and you'll refactor more often)
- you'll be "that guy/gal that uses vim for everything"
- you may lose childhood memories as you become more proficient with vim trying remember all the shortcut's you've created
- until this process is fully baked, you may have to "visit the mothership" to do more complex project and solution mainpulations

##Getting your "dev" environment setup on Windows

The setup is still pretty manual. As this evolves, ideally there will be a chocolatey package that will get your entire environment up and running. For now this read me will have to do...

- install [msysgit](https://code.google.com/p/msysgit/downloads/list)

This is what will add vim to your system.  Keep in mind that this is vim and not gVim.

- install [chocolatey](http://chocolatey.org/)

It's apt-get for Windows.

- install gVim via chocolatey by running: cinst vim

This will set up files needed for Vim customization

- install [ruby 1.9.3](http://rubyinstaller.org/downloads/)

Be sure to add it to your PATH, ruby is used for rake (build automation), warmup (solution/project generation) and nokogiri (xml file/csproj manipulation)

- install [ctags for Windows](http://sourceforge.net/projects/ctags/files/ctags/) extract to a directory and add that directory to your PATH

Ctags is used for auto completion and "go to definition" in vim.

- install [Growl for Windows](http://www.growlforwindows.com/gfw/)

This will give you notifications of when builds and tests fail. Open up Growl once so that the C:\Users\%USER%\AppData\Local\Growl\2.0.0.0\Displays\ directory gets created, then...

- install [Translucent Dark](http://softwarebakery.com/frozencow/translucentdark.html), extact the theme to C:\Users\%USER%\AppData\Local\Growl\2.0.0.0\Displays\TranslucentDark

This is a really nice theme for Growl for Windows. [Here are the settings I use](http://i.imgur.com/buWyf.png).

- install [ConEmu](http://sourceforge.net/projects/conemu/)

This is an incredibly awesome tabbed and split console window manager. We'll customize everything in the next section.

- install [Strawberry Perl](http://strawberryperl.com/)

This is needed to for a package called ack (and of course opens you up to using packages built in perl). Ack provides a very nice way to search for text in a directory.

##Installing packages

- from the command line run: gem install warmup

This will install a templating engine used to create .Net solutions

- from the command line run: gem install nokogiri

This will install an xml manipulation library used to mainpulate project and solution files

- from the command line run: ppm install ack

This will install ack, a powerful perl based text search tool

- download [pathogen](https://github.com/tpope/vim-pathogen) as a zip, then extract the files and copy the autoload folder to C:\Program Files (x86)\vim\vim73

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

C:\Windows\SysWOW64\cmd.exe /c ""C:\Program Files (x86)\Git\bin\sh.exe" --login -i" -cur_console:as33V  -new_console:d:{YOURSTARTUPDIRECTORY}
</pre>

- and then add set the script to run at startup

<a href="http://imgur.com/29PxiNP"><img src="http://i.imgur.com/29PxiNP.png" title="Hosted by imgur.com"/></a>

- change this key binding from Ctrl + V to Shift + Ctrl + V

<a href="http://imgur.com/aZlRVzH"><img src="http://i.imgur.com/aZlRVzH.png" title="Hosted by imgur.com"/></a>


