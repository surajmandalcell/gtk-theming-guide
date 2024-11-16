## Creating Icon Theme

Not only can Linux users customize the desktop theme, but they can also change the icons. Icon-theme packs are easy to make, install, and obtain. Many Linux users may find it helpful to learn how to change icons, edit them, get more, etc.

## Icon Location  

Icons may be stored in "~/.icons" or "/usr/share/icons". Icons that are in "~/.icons" are only accessible to the owner of that home folder. While icons in "/usr/share/icons" are global-icons that are accessible by all users. "/usr/share/pixmaps" contains icons that are installed or used by various applications and software packages.

## Icon Searching  

Applications that are looking for an icon will first look in "~/.icons". Next, the application will try "/usr/share/icons", and then "/usr/share/pixmaps".

## Icon Theme  

An icon theme has a specific structure/format that must be used to create a usable icon-pack. Inside the icon directories ("~/.icons" and "/usr/share/icons"), each icon theme has its own folder that is named after the icon-theme. Within the icon-theme's directory are several folders and some important files. For instance, an icon-theme may contain the below listed directories and files.
Directories

  * 8x8
  * 16x16
  * 22x22
  * 24x24
  * 32x32
  * 48x48
  * 52x52
  * 128x128
  * 240x240
  * 256x256
  * 512x512
  * scalable
  * scalable-up-to-32
  * Files
  * AUTHORS
  * CONTRIBUTORS
  * COPYING
  * cursor.theme
  * icon-theme.cache
  * index.theme
  * Adwaita-Icon-Theme-Folder.jpg

The directories contain images and icons with the specified dimensions used as the folder names (in pixels).

However, "scalable" and "scalable-up-to-32" contain SVG files. The SVG files in "scalable-up-to-32" can be used without issues when used at 32-pixels or below. Within each directory are more folders as listed and described below. Each of these sub-directories may contain SVG, PNG, or XPM files (PNG is recommended).

 Each file must use a particular name so that the desktop system can find the icon that it needs. Soft-links (shortcuts) are permitted because they allow developers to create one image that can be the icon for many uses (such as using the same image for all types of mount optical disks).
 
 To learn more about the filenames for icons, refer to the naming specification - [freedesktop referance page](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html)


- actions - Icons for actions (such as redo, close, play, etc.) that may be seen in toolbars, menus, buttons, etc.
- animations - Images that are used to make animated icons (such as "loading spinners" or disc-burning progress)
- apps - Icons for specific applications or for applications of a general type
- categories - Icons for various application categories
- devices - Icons for devices such as mounted storage media, optical disks, iPods, phones, printers, etc.
- emblems - Icons for tags and file properties (such as the "unreadable" or "soft-link" symbol)
- emotes - Emoticons/Emojis
- International - Icons representing different languages/nations
- mimetypes (or mimes) - Icons for various mimetypes; these are typically used as the icons for files
- places - Icons for folders, servers, trash-bin, etc.
- search - Images for search-related icons
- status - Icons used for notifications (like "error", "warning", etc.), battery level, audio volume, network status, etc.
- stock - Miscellaneous
- web - Icons for web-apps (like the web-apps commonly seen in the Unity dashboard)

The icon images themselves can be made using Gimp (when making PNG files) and Inkscape (when making SVG files). All icon images must be a perfect square. Thus, the "32x32" icons must be 32 pixels tall and 32 pixels wide. RGBa is recommended, especially for the transparency layer (alpha-channel).

Some icon-themes (like "Humanity") use a slightly different format. The "Humanity" icon-pack contains folders for each icon context (emotes, devices, places, etc.) and then the different sizes as sub-directories. The sub-directories for each icon size uses the name format "22" rather than "22x22".

The files in the root of the icon-theme each have a particular purpose as described below.

AUTHORS - List of authors and possibly their contact information and website

CONTRIBUTORS - List of people that helped with the project

COPYING - The license (such as GPL)

cursor.theme - Cursor-theme information

icon-theme.cache - Icon cache that are used as memory mapped files; the files directly map the icons files, thus reducing the time to find a needed icon

index.theme - The icon-theme description file; encoded in UTF-8

FUN FACT: The "gtk-update-icon-cache" command can be used to update/refresh the icon cache files.

Sample index.theme
Code:
```
[Icon Theme]
Name=Theme_Name
Name[ca]=Translated_Name
Name[cs]=Translated_Name
Name[da]=Translated_Name
Comment=Theme_Description
Comment[ca]=Translated_Theme_Description
Comment[cs]=Translated_Theme_Description
Comment[da]=Translated_Theme_Description
Inherits=Name_a_Theme_to_use_as_a_Fallback
```
  
## KDE specific settings
```
DisplayDepth=32
LinkOverlay=link_overlay
LockOverlay=lock_overlay
ZipOverlay=zip_overlay
DesktopDefault=48
DesktopSizes=16,22,32,48,64,72,96,128
ToolbarDefault=22
ToolbarSizes=16,22,32,48
MainToolbarDefault=22
MainToolbarSizes=16,22,32,48
SmallDefault=16
SmallSizes=16
PanelDefault=32
PanelSizes=16,22,32,48,64,72,96,128
```

## List all directories
```
Directories=8x8/emblems,16x16/actions,16x16/apps,
```


## Specify the context, size, and type of each directory
```
[8x8/emblems]
Context=Emblems
Size=8
Type=Fixed
```
Installing and Removing Icons
Icon themes can be installed by placing the icon-pack in one of the proper icon directories. If the icons are placed in "/usr/share/icons", then ensure that the owner is "Root" and the proper permissions are set so that all users can read the files.

To recursively set the proper permissions and ownership to all folders and files in the icon-pack, execute the below commands. Open a terminal in "/usr/share/icons" before executing the commands.


Code:
```
chown -R root:root ./THEME_NAME
find ./THEME_NAME -type d -exec chmod 755 {} \;
find ./THEME_NAME -type f -exec chmod 644 {} \;
```
NOTE: Directories must use "755" permissions (drwxr-xr-x) and files must use "644" permissions (rw-r--r--). This is better for security while ensuring that users and programs can access the data.

To remove icon themes, delete the icon-pack's directory.

Obtaining Icons

Icons can be obtained via the repositories or from various websites.

GNOME-Look - http://gnome-look.org/index.php?xcontentmode=120x121

Noobs Lab - http://www.noobslab.com/p/themes-icons.html

Changing Icons
Most theme changers also provide an interface for changing the icons. Such applications include "Ubuntu Tweak", "Unity Tweak Tool", "Appearance", and others.

## Cursors

Cursors are also found in "~/.icons" and "/usr/share/icons". Cursor-themes use a similar format. However, the folder contains a "cursors" directory and two files - "cursor.theme" and "index.theme". Inside of the "cursors" directory are files that are each named after each type of cursor (top_left_corner, help, move, grabbing, etc.).

These files are "X11 cursor images" and they have the "image/x-xcursor" mimetype. This type of image file contains multiple images. Each contained image is 48, 32, and 24 pixels in height and width; the images support the alpha-layer (transparency/RGBa). Gimp supports X11 cursor images and represents the contained sub-images as different layers. Each layer must be named using the format "(SIZEpx)_1 (50ms) (replace)", where "SIZE" is the width/height in pixels.

All cursors that are drawn in these images must be in the center of the space (whether the space be 48x48 pixels or some other size).
