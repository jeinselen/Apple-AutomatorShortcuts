# Apple-AutomatorShortcuts
Assorted Apple Shortcuts to speed up media processing and other tasks, provided as-is.

Many of the shortcuts require specific command line tools to be installed, making them unsuitable for usage outside of tech art environments (and except for special cases, unusable on iOS devices).



## Image and Video shortcuts for MacOS Requirements

### Step 1: Install CLI management (Xcode and MacPorts)

1. Install Xcode from the Mac App Store
   - https://apps.apple.com/us/app/xcode/id497799835?mt=12
2. Accept the Xcode command line license in the Terminal
   - `sudo xcodebuild -license accept`
3. Download the MacPorts installer and install
   - https://www.macports.org/install.php

You can also use HomeBrew, but while it's super popular among programmers, it may not have the same diversity of tool options. I typically use both, but rely on MacPorts for managing most of my imagery/media centred CLI utilities.

To maintain MacPorts and all of the tools installed by it, you can use the following lines in the Terminal periodically (if everything is working, updates probably don't matter, but I typically keep everything current).

- `sudo port selfupdate`
  - This updates MacPorts itself and the list of ports (applications that can be installed)
  - `sudo` is dangerous but necessary…enter your admin password and trust you didn't accidentally type `rm *` or something else truly devastating
- `sudo port upgrade outdated`
  - This will update all of the installed ports to the lateste versions available via MacPorts
- `sudo port reclaim`
  - This removes the previous versions of programs that have been updated and clears up the build folders
  - When asked, I don't let it remind me…it's annoying when it pops up EVERY TIME



### Step 2: Install Command Line Interfaces

- `sudo port install ffmpeg +nonfree`
  - This installs FFmpeg! Yay! And the [Blender Render Kit extension](https://github.com/jeinselen/Blender-RenderKit) should automatically detect it once installed, so this takes care of multiple toolsets simultaneously
  - The `+nonfree` modifier adds AAC audio support…probably not necessary, but doesn't hurt to have just in case
- `sudo port install imagemagick7`
  - This installs ImageMagick for image processing, but after installation the following lines are needed for it to actually work (and be detected by [Blender Render Kit](https://github.com/jeinselen/Blender-RenderKit) for extending UV map edges after rendering a material node to an image)
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/animate /opt/local/bin/animate`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/compare /opt/local/bin/compare`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/composite /opt/local/bin/composite`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/conjure /opt/local/bin/conjure`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/convert /opt/local/bin/convert`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/display /opt/local/bin/display`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/identify /opt/local/bin/identify`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/import /opt/local/bin/import`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/magick /opt/local/bin/magick`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/mogrify /opt/local/bin/mogrify`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/montage /opt/local/bin/montage`
  - `sudo ln -s  /opt/local/lib/ImageMagick7/bin/stream /opt/local/bin/stream`
- `sudo port install gifsicle`
  - If you ever need to create GIF files from video files…this'll help create the smallest possible files!



### Step 3: Import Shortcuts

Open up the Shortcuts app (included with MacOS) and import any of the shortcut files needed. Here are a few notable ones:

- FF Convert

  - This is the main event, and has seen constant use for well over a decade (first via Apple Automator, now Apple Shortcuts)
  - The two options I added last year specifically for BCON are `Cropped 1080p` and `Padded 1080p`
  - This is also how I create any files I'm uploading to Vimeo, or sending to clients, or posting in Slack…
- FF Convert MP4
  - This is relatively new, I wanted something that let me fine-tune compression settings a little more…not necessary, but if you want individual options for size, video quality, and audio bitrate, this is the one to use (but probably not for BCON, it doesn't have cropping/padding options)
- FF ProConvert
  - If you have a weird file format you want to open in QuickTime, or something that'll be WAY easier to edit, or just save out a smaller-but-still-not-bad ProRes LT format, this is the tool to use
- FF Sequence
  - Right-click any one (or more) image in an animation sequence to turn it into a video…that's it
  - Options are fairly similar to FF Convert
- FF Convert Audio
  - Does what it says on the package, this is what I use for any Unity audio deliveries (render out of Reaper as WAV of AIFF, then compress using these presets)
- Blender Project Version
  - Gives you the version of Blender that a project file was last saved in…helpful when you're opening up an old project and don't want to deal with compatibility issues and deprecated features!
- Blender Extension List
  - When actioned on a folder containing valid Blender Extension .zip files, creates the .html and .json format files necessary to host the extensions on your own server
  - Example: [Launch Blender Extensions on GitHub](https://github.com/jeinselen/Launch-Blender-Extensions)



### Step 4: Enable Shortcuts

Now that you've imported shortcuts, you will probably need to enable them in some way. This is frustratingly not automatic, but not difficult. Just tedious.

1. Double-click a shortcut to open it up, navigate to the Info > Details panel, and ensure "Use as Quick Action", "Finder", and "Services Menu" options are checked
   - There's a Shortcuts icon in the menu bar as well, most of the shortcuts include an option to choose a file instead of operating on whatever file(s) were right-clicked on in the Finder…you can turn on "Pin in Menu Bar" if you want a quick way to access shortcuts without ever switching to the Finder
2. If they were already checked and they're not showing up in the right-click menu in Finder, then we have to manually turn them on. Ugh. MacOS has definitely gotten more complicated over the years. Used to be you just copied an Automator action into a library folder and that was it…anyway, two ways to do this:
   1. From the context menu, choose "customise" and enable/disable as needed (same settings panel as below, just faster access!)
   2. System Settings > General > Login Items & Extensions > (scroll down) Finder, then click the "I" button to customise what is and isn't enabled (perfect time to disable stuff you don't want in the list too)
