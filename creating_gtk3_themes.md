## Tools Required/Helpful

 1. **GtkInspector** is a must have tool if you want to make gtk themes or style gtk apps. GtkInspector is the built-in interactive debugging support in GTK+. It was added in GTK+ 3.14, based on a copy of the well-estabished gtkparasite. This tool is integerated natively into gnome desktop environment but disabled by default. To use this you need to follow these steps :
    ```sh
    gsettings set org.gtk.Settings.Debug enable-inspector-keybinding true
     ```
     launch it by pressing on the keyboard Control-Shift-I or Control-Shift-D.
    If you don't want to use the shortcuts, you can also run it temporarily directly when running your app with:
    
    ```sh
    GTK_DEBUG=interactive your-app
    ```
    If you get `No such schema 'org.gtk.Settings.Debug'` then install the `libgtk-3-dev` dependency by using
    ```sh
    sudo apt-get install libgtk-3-dev
    ```
 2. **Color picker** - You can use any color picker you want (gnome-color-picker, elementary color picker, etc.) as long as you have one its fine.
 3. **Good text editor** - You might want to consider using good text editor for syntax hilighting and auto-complete for faster css.

## Study A Premade GTK3 Theme

To create a GTK3 theme, developers can start with an empty file or they can use a pre-existing theme as a template. It may help beginners to start with a pre-existing theme. For instance, a theme can be copied to the user's home folder and then the developer can start editing the files.

The general format for a GTK3 theme is to create a folder named after the theme. Then, create a sub-directory called "gtk-3.0" and create a file inside of it named "gtk.css". In the "gtk.css" file, use CSS code to control how the theme will look. Move the theme to ~/.themes for testing purposes. Use the newly created theme and make changes as necessary. If desired, developers can add additional components to the theme for GTK2, Openbox, Metacity, Unity, etc.

> To explain how to create themes, we will study the "Ambiance" theme, which is usually found at /usr/share/themes/Ambiance. This directory contains the below listed sub-directories and a file named "index.theme".

- gtk-2.0
- gtk-3.0
- metacity-1
- unity

<br />
"**index.theme**" contains metadata (such as the theme's name) and some important settings (such as the button layout). Below is the "index.theme" file for "Ambiance".

code :
```sh
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Ambiance
Comment=Ubuntu Ambiance theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Ambiance
MetacityTheme=Ambiance
IconTheme=ubuntu-mono-dark
CursorTheme=DMZ-White
ButtonLayout=close,minimize,maximize:
X-Ubuntu-UseOverlayScrollbars=true
```

<br />


The "**gtk-3.0**" directory contains files for GTK3. Instead of "gtkrc", GTK3 uses "gtk.css" as the main theme file. In the Ambiance theme, the file contains one line - '@import url("gtk-main.css");'. The "settings.ini" file contains important theme-wide settings. GTK3 themes use an "apps" directory for the same purpose as GTK2. The "assets" directory contains images for radio buttons, check-boxes, etc. Below are the contents of /usr/share/themes/Ambiance/gtk-3.0/gtk-main.css

code :

```css
/*default color scheme */
@define-color bg_color #f2f1f0;
@define-color fg_color #4c4c4c;
@define-color base_color #ffffff;
@define-color text_color #3C3C3C;
@define-color selected_bg_color #f07746;
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #000000;
@define-color tooltip_fg_color #ffffff;

/* misc colors used by gtk+
 *
 * Gtk doesn't currently expand color variables for style properties. Thus,
 * gtk-widgets.css uses literal color names, but includes a comment containing
 * the name of the variable. Please remember to change values there as well
 * when changing one of the variables below.
 */
@define-color info_fg_color rgb (181, 171, 156);
@define-color info_bg_color rgb (252, 252, 189);
@define-color warning_fg_color rgb (173, 120, 41);
@define-color warning_bg_color rgb (250, 173, 61);
@define-color question_fg_color rgb (97, 122, 214);
@define-color question_bg_color rgb (138, 173, 212);
@define-color error_fg_color rgb (235, 235, 235);
@define-color error_bg_color rgb (223, 56, 44);
@define-color link_color @selected_bg_color;
@define-color success_color #4e9a06;
@define-color error_color #df382c;

/* theme common colors */
@define-color button_bg_color shade (@bg_color, 1.02); /*shade (#cdcdcd, 1.08);*/
@define-color notebook_button_bg_color shade (@bg_color, 1.02);
@define-color button_insensitive_bg_color mix (@button_bg_color, @bg_color, 0.6);
@define-color dark_bg_color #3c3b37;
@define-color dark_fg_color #dfdbd2;

@define-color backdrop_fg_color mix (@bg_color, @fg_color, 0.8);
@define-color backdrop_text_color mix (@base_color, @text_color, 0.8);
@define-color backdrop_dark_fg_color mix (@dark_bg_color, @dark_fg_color, 0.75);
/*@define-color backdrop_dark_bg_color mix (@dark_bg_color, @dark_fg_color, 0.75);*/
@define-color backdrop_selected_bg_color shade (@bg_color, 0.92);
@define-color backdrop_selected_fg_color @fg_color;

@define-color focus_color alpha (@selected_bg_color, 0.5);
@define-color focus_bg_color alpha (@selected_bg_color, 0.1);

@define-color shadow_color alpha(black, 0.5);

@define-color osd_fg_color #eeeeec;
@define-color osd_bg_color alpha(#202526, 0.7);
@define-color osd_border_color alpha(black, 0.7);

@import url("gtk-widgets-borders.css");
@import url("gtk-widgets-assets.css");
@import url("gtk-widgets.css");
@import url("apps/geary.css");
@import url("apps/unity.css");
@import url("apps/baobab.css");
@import url("apps/gedit.css");
@import url("apps/nautilus.css");
@import url("apps/gnome-panel.css");
@import url("apps/gnome-terminal.css");
@import url("apps/gnome-system-log.css");
@import url("apps/unity-greeter.css");
@import url("apps/glade.css");
@import url("apps/california.css");
@import url("apps/software-center.css");
@import url("public-colors.css");
```

<br>

The "**gtk-2.0**" directory contains files for GTK2 such as a "gtkrc" file and an "apps" directory that contains application-specific GTK settings. The "gtkrc" file is the main CSS-file for the GTK2 portion of the theme. Below are the contents of /usr/share/themes/Ambiance/gtk-2.0/apps/nautilus.rc

code :
```css
# ==============================================================================
# NAUTILUS SPECIFIC SETTINGS
# ==============================================================================

style "nautilus_info_pane" {
   bg[NORMAL] = @bg_color
}

widget_class "*Nautilus*<GtkNotebook>*<GtkEventBox>" style "nautilus_info_pane"
widget_class "*Nautilus*<GtkButton>" style "notebook_button"
widget_class "*Nautilus*<GtkButton>*<GtkLabel>" style "notebook_button"
```

<br>

The "**metacity-1**" folder contains images that the Metacity window-manager uses for buttons (such as the "close window" button). This directory also contains a file named "metacity-theme-1.xml" that contain's the theme's metadata (like the developer's name) and styling. However, the Metacity portion of the theme uses XML rather than CSS.

Some themes may contain other directories. For instance, "**xfwm4**". The "xfwm4" directory contains `*`.xpm files, `*`.png images (in the "png" folder), a "README" file, and a "themerc" file which contains settings (as seen below).

```sh
/usr/share/themes/Clearlooks-Phenix/xfwm4/themerc
```

code :
```md
# Clearlooks XFWM4 by Casey Kirsle

show_app_icon=true
active_text_color=#FFFFFF
inactive_text_color=#939393
title_shadow_active=frame
title_shadow_inactive=false
button_layout=O|HMC
button_offset=2
button_spacing=2
full_width_title=true
maximized_offset=0
title_vertical_offset_active=1
title_vertical_offset_inactive=1
```

<br />



## Importing style sheets

GTK+ supports the CSS @import rule, in order to load another style sheet in addition to the currently parsed one.

The syntax for @import rules is as follows:

〈import rule〉 = @import [ 〈url〉 | 〈string〉 ]
〈url〉 = url( 〈string〉 )

> An example for using the @import rule

```css
   @import url("path/to/common.css");
```



## Selectors

Selectors work very similar to the way they do in CSS.  

All widgets have one or more CSS nodes with element names and style classes. When style classes are used in selectors, they have to be prefixed with a period. Widget names can be used in selectors like IDs. When used in a selector, widget names must be prefixed with a # character.  

In more complicated situations, selectors can be combined in various ways. To require that a node satisfies several conditions, combine several selectors into one by concatenating them. To only match a node when it occurs inside some other node, write the two selectors after each other, separated by whitespace. To restrict the match to direct children of the parent node, insert a > character between the two selectors.  

### Examples



**Theme labels that are descendants of a window**

```css
window label {
 background-color: #898989;
}
```
  

**Theme notebooks, and anything within**

```css
notebook {
 background-color: #a939f0;
}
```
  

**Theme combo boxes, and entries that are direct children of a notebook**

```css
combobox,
notebook > entry {
 color: @fg_color;
 background-color: #1209a2;
}
```
  

**Theme any widget within a GtkBox**

```css
box *  {
 font: 20px Sans;
}
```
  

**Theme a label named title-label**

```css
label#title-label {
 font: 15px Sans;
}
```
  

**Theme any widget named main-entry**

```css
#main-entry {
 background-color: #f0a810;
}
```
  

**Theme all widgets with the style class entry**

```css
.entry {
 color: #39f1f9;
}
```
  

**Theme the entry of a GtkSpinButton**

```css
spinbutton entry {
 color: #900185;
}
```
  

It is possible to select CSS nodes depending on their position amongst their siblings by applying pseudo-classes to the selector, like :first-child, :last-child or :nth-child(even). When used in selectors, pseudo-classes must be prefixed with a : character.

**Theme labels in the first notebook tab**

```css
notebook tab:first-child label {
 color: #89d012;
}
```
  

> Another use of pseudo-classes is to match widgets depending on their state. The available pseudo-classes for widget states are :active, :hover :disabled, :selected, :focus, :indeterminate, :checked and :backdrop. In addition, the following pseudo-classes don't have a direct equivalent as a widget state: :dir(ltr) and :dir(rtl) (for text direction), :link and :visited (for links) and :drop(active) (for highlighting drop targets). Widget state pseudo-classes may only apply to the last element in a selector. 

**Theme pressed buttons**

```css
button:active {
 background-color: #0274d9;
}
```
  

**Theme buttons with the mouse pointer over it**

```css
button:hover {
 background-color: #3085a9;
}
```
  

**Theme insensitive widgets**

```css
*:disabled {
 background-color: #320a91;
}
```
  

**Theme checkbuttons that are checked**

```css
checkbutton:checked {
 background-color: #56f9a0;
}
```
  

**Theme focused labels**

```css
label:focus {
 background-color: #b4940f;
}
```
  

**Theme inconsistent checkbuttons**

```css
checkbutton:indeterminate {
 background-color: #20395a;
}
```


  

To determine the effective style for a widget, all the matching rule sets are merged. As in CSS, rules apply by specificity, so the rules whose selectors more closely match a node will take precedence over the others.

The full syntax for selectors understood by GTK+ can be found in the table below. The main difference to CSS is that GTK+ does not currently support attribute selectors.



### A table of selectors used by gtk+ to style apps

| Pattern  | Matches | Reference  | Notes |
|---|---|---|---|
|*  | any node |  CSS |  |
| E  |   any node with name E  |  CSS    | |
| E.class  |   any E node with the given style class  | CSS    | |
| E#id  |   any E node with the given ID  | CSS |  GTK+ uses the widget name as ID |
| E:nth-child({nth-child})  | any E node which is the n-th child of its parent node   | CSS | |
| E:nth-last-child({nth-child})  |  any E node which is the n-th child of its parent node, counting from the end  | CSS | |
| E:first-child  |   any E node which is the first child of its parent node  | CSS | |   
| E:last-child  | any E node which is the last child of its parent node  |  CSS | |   
| E:only-child  | any E node which is the only child of its parent node   | CSS   | Equivalent to E:first-child:last-child |
| E:link, E:visited  |  any E node which represents a hyperlink, not yet visited (:link) or already visited (:visited) | CSS  | Corresponds to GTK_STATE_FLAG_LINK and GTK_STATE_FLAGS_VISITED |
| E:active, E:hover, E:focus  |  any E node which is part of a widget with the corresponding state  |  CSS  | Corresponds to GTK_STATE_FLAG_ACTIVE, GTK_STATE_FLAG_PRELIGHT and GTK_STATE_FLAGS_FOCUSED; GTK+ also allows E:prelight and E:focused |
| E:disabled  |   any E node which is part of a widget which is disabled  | CSS  | Corresponds to GTK_STATE_FLAG_INSENSITIVE; GTK+ also allows E:insensitive |
| E:checked  | any E node which is part of a widget (e.g. radio- or checkbuttons) which is checked   | CSS  |  Corresponds to GTK_STATE_FLAG_CHECKED |
| E:indeterminate  | any E node which is part of a widget (e.g. radio- or checkbuttons) which is in an indeterminate state  |  CSS3, CSS4 |  Corresponds to GTK_STATE_FLAG_INCONSISTENT; GTK+ also allows E:inconsistent |
| E:backdrop, E:selected  |   any E node which is part of a widget with the corresponding state  |  -  | Corresponds to GTK_STATE_FLAG_BACKDROP, GTK_STATE_FLAG_SELECTED |
| E:not({selector})  |  any E node which does not match the simple selector {selector}  |  CSS   | |
| E:dir(ltr), E:dir(rtl)  |   any E node that has the corresponding text direction  | CSS4   | |
| E:drop(active)  |  any E node that is an active drop target for a current DND operation  |  CSS4   | |
| E F  | any F node which is a descendent of an E node  | CSS    | |
| E > F  |  any F node which is a child of an E node | CSS    | |
| E ~ F  |  any F node which is preceded by an E node  |  CSS  | |
| E + F  |  any F node which is immediately preceded by an E node  |  CSS   | |

To learn more about selectors in CSS, read the Selectors [module](https://www.w3.org/TR/css3-selectors/) of the CSS specification.


## Colors

CSS allows to specify colors in various ways, using numeric values or names from a predefined list of colors. 

**Specifying colors in various ways**  

```css
   color: transparent;
   background-color: red;
   border-top-color: rgb(128,57,0);
   border-left-color: rgba(10%,20%,30%,0.5);
   border-right-color: #ff00cc;
   border-bottom-color: #ffff0000cccc;
```

**An example for defining colors**

 GTK+ adds several additional ways to specify colors.

{gtk color} = {symbolic color} | {color expression} | {win32 color}

The first is a reference to a color defined via a @define-color rule. The syntax for @define-color rules is as follows:

{define color rule} = @define-color {name} {color}

To refer to the color defined by a @define-color rule, use the name from the rule, prefixed with @.

{symbolic color} = @{name}

```css
@define-color bg_color #f9a039;

* {
  background-color: @bg_color;
}
```

## Testing Themes

When creating themes, it may be helpful to test it and tweak the code to get the desired appearance. Such developers may want to use some type of "theme-previewer". Thankfully, some exist.

 - GTK+ Change Theme - This program can change the GTK theme and allow
   developers to preview the theme. The program is composed of one
   window that contains many widgets, thus providing a complete preview
   for the theme. To install this program, type "apt-get install
   gtk-chtheme".
 - GTK Theme Switch - This program allows users to easily change the
   user's theme. Be sure to have some applications open to view and test
   the theme. To install this program, type "apt-get install
   gtk-theme-switch" and type "gtk-theme-switch2" in a terminal to run
   it.
 - LXappearance - This program can change themes, icons, and fonts. PyWF
 - This is a Python-based alternative to "The Widget Factory". PyWF can be obtained at
   http://gtk-apps.org/content/show.php/PyTWF?content=102024
 - The Widget Factory - This is an old GTK-previewer. To install this program, type
   "apt-get install thewidgetfactory" and type "twf" in a terminal to
   run it.

<br /><br />

## Theme Downloads

 - Cinnamon - http://gnome-look.org/index.php?xcontentmode=104
 - Compiz - http://gnome-look.org/index.php?xcontentmode=102
 - GNOME Shell - http://gnome-look.org/index.php?xcontentmode=191
 - GTK2 - http://gnome-look.org/index.php?xcontentmode=100
 - GTK3 - http://gnome-look.org/index.php?xcontentmode=167
 - KDE/Qt -
   http://kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16
 - Linux Mint Themes -
   http://linuxmint-art.org/index.php?xcontentmode=9x14x100
 - Metacity - http://gnome-look.org/index.php?xcontentmode=101
 - Ubuntu Themes - http://www.ubuntuthemes.org/

<br />

## Further Reading
   
 - Gtk+ CSS Overview - https://developer.gnome.org/gtk3/stable/chap-css-overview.html
 - Graphical User Interface (GUI) Reading Guide -
   http://www.linux.org/threads/gui-reading-guide.6471/
 - GTK - http://www.linux.org/threads/understanding-gtk.6291/
 - Introduction to Glade -
   http://www.linux.org/threads/introduction-to-glade.7142/
 - Desktop Environment vs Window Managers -
   http://www.linux.org/threads/desktop-environment-vs-window-managers.7802/
 - Official GTK+ 3 Reference Manual -
   https://developer.gnome.org/gtk3/stable/
 - GtkCssProvider -
   https://developer.gnome.org/gtk3/stable/GtkCssProvider.html