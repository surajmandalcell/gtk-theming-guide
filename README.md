# Linux-Theming-Documentation

##If you are a linux user and unsatisfied with the current theme collection want to create new theme or modify current one then this documentation is for you
<br />
Many Linux desktops supporting themes. A theme is a particular appearance or "****" for the GUI. Users can change the theme to make the desktop look different. Usually, users also change the icons. However, the theme and icon-pack are two separate entities. Numerous people want to make their own theme, so here is an article about making GTK themes as well as various essential information.

NOTE: This article primarily focuses on GTK3, but it will discuss a little about GTK2, Metacity, and others. Cursors and icons will not be discussed in this article.
<br />
### Basic Concepts

The GIMP ToolKit (GTK) is a widget-toolkit used to create GUIs on a variety of systems (thus making GTK cross-platform). GTK (http://www.gtk.org/) is commonly and incorrectly thought to stand for "GNOME ToolKit", but is actually stands for "GIMP ToolKit" because it was first created to design an user interface for GIMP. GTK is an object-oriented toolkit written in C (GTK itself is not a language). GTK is entirely open-source under the LGPL license. GTK is a widely used toolkit for GUIs and many tools are available for GTK.

Themes made for GTK will not work in Qt-based applications. A Qt-theme is needed to apply a theme to Qt applications.

The themes use Cascading Style-Sheets (CSS) to generate the theme's appearance. This is the same CSS that web-developers use on web-pages. However, instead of HTML tags being referenced, GTK widgets are specified. It is important that theme developers learn CSS.
<br />
### Theme Location

Themes may be stored in "~/.themes" or "/usr/share/themes". Themes that are in "~/.themes" are only accessible to the owner of that home folder. While themes in "/usr/share/themes" are global-themes that are accessible by all users. When a GTK application executes, it has a list of possible theme files that it checks in a specific order. If the theme file is not found, then it will try the next file on the list. Below is the list in the order that GTK3 applications try to use.

	

 

    $XDG_CONFIG_HOME/gtk-3.0/gtk.css (typically
       ~/.config/gtk-3.0/gtk.css)
    
        
      ~/.themes/NAME/gtk-3.0/gtk.css
    
    	
      $datadir/share/themes/NAME/gtk-3.0/gtk.css (typically
       /usr/share/themes/name/gtk-3.0/gtk.css)

***NOTE***: "**NAME**" is a placeholder for the name of the current theme.

If there are two themes with the same name, then the one in the user's home folder (~/.themes) will be used. Developers can take advantage of GTK's theme-seeking algorithm by testing new themes in their local home's theme directory.
<br />
### Theme Engines

A "Theme engine" is a piece of software that changes the look of the GUI's widgets. The engine reads and uses the theme's files to know how the various widgets should be drawn. Some engines come with themes of their own. Each engine has its advantages and disadvantages, and some engines add special properties and features.

Many theme-engines can be obtained from the default repositories. Debian-based Linux distros can execute "apt-get install gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico" to install three different engines. Many engines are available for both GTK2 and GTK3. Below is a small list of examples.

- gtk2-engines-aurora - Aurora GTK2 engine
- gtk2-engines-pixbuf - Pixbuf GTK2 engine
- gtk3-engines-oxygen - Engine port of the Oxygen widget style to GTK
- gtk3-engines-unico - Unico GTK3 engine
- gtk3-engines-xfce - GTK3 engine for Xfce

<br />

### Creating GTK3 Themes

To create a GTK3 theme, developers can start with an empty file or they can use a pre-existing theme as a template. It may help beginners to start with a pre-existing theme. For instance, a theme can be copied to the user's home folder and then the developer can start editing the files.

The general format for a GTK3 theme is to create a folder named after the theme. Then, create a sub-directory called "gtk-3.0" and create a file inside of it named "gtk.css". In the "gtk.css" file, use CSS code to control how the theme will look. Move the theme to ~/.themes for testing purposes. Use the newly created theme and make changes as necessary. If desired, developers can add additional components to the theme for GTK2, Openbox, Metacity, Unity, etc.

To explain how to create themes, we will study the "Ambiance" theme, which is usually found at /usr/share/themes/Ambiance. This directory contains the below listed sub-directories and a file named "index.theme".

- gtk-2.0
- gtk-3.0
- metacity-1
- unity

"**index.theme**" contains metadata (such as the theme's name) and some important settings (such as the button layout). Below is the "index.theme" file for "Ambiance".

code :

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

The "**gtk-2.0**" directory contains files for GTK2 such as a "gtkrc" file and an "apps" directory that contains application-specific GTK settings. The "gtkrc" file is the main CSS-file for the GTK2 portion of the theme. Below are the contents of /usr/share/themes/Ambiance/gtk-2.0/apps/nautilus.rc

code :

    # ==============================================================================
    # NAUTILUS SPECIFIC SETTINGS
    # ==============================================================================
    
    style "nautilus_info_pane" {
       bg[NORMAL] = @bg_color
    }
    
    widget_class "*Nautilus*<GtkNotebook>*<GtkEventBox>" style "nautilus_info_pane"
    widget_class "*Nautilus*<GtkButton>" style "notebook_button"
    widget_class "*Nautilus*<GtkButton>*<GtkLabel>" style "notebook_button"

----------

Credits : This article was taken from [this](http://www.linux.org/threads/installing-obtaining-and-making-gtk-themes.8463/) link



