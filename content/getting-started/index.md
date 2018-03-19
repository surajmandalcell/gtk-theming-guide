---
date: 2016-03-09T00:11:02+01:00
title: Getting started
weight: 10
---

## Basic Concepts

The GIMP ToolKit (GTK) is a widget-toolkit used to create GUIs on a variety of systems (thus making GTK cross-platform). GTK (http://www.gtk.org/) is commonly and incorrectly thought to stand for "GNOME ToolKit", but is actually stands for "GIMP ToolKit" because it was first created to design an user interface for GIMP. GTK is an object-oriented toolkit written in C (GTK itself is not a language). GTK is entirely open-source under the LGPL license. GTK is a widely used toolkit for GUIs and many tools are available for GTK.

Themes made for GTK will not work in Qt-based applications. A Qt-theme is needed to apply a theme to Qt applications.

The themes use Cascading Style-Sheets (CSS) to generate the theme's appearance. This is the same CSS that web-developers use on web-pages. However, instead of HTML tags being referenced, GTK widgets are specified. It is important that theme developers learn CSS.

## Theme Location

```sh
$XDG_CONFIG_HOME/gtk-3.0/gtk.css (typically ~/.config/gtk-3.0/gtk.css)

  
~/.themes/NAME/gtk-3.0/gtk.css 


$datadir/share/themes/NAME/gtk-3.0/gtk.css (typically
 /usr/share/themes/name/gtk-3.0/gtk.css)
```

***NOTE***: "**NAME**" is a placeholder for the name of the current theme.

If there are two themes with the same name, then the one in the user's home folder (~/.themes) will be used. Developers can take advantage of GTK's theme-seeking algorithm by testing new themes in their local home's theme directory.

### Theme Engines

A "Theme engine" is a piece of software that changes the look of the GUI's widgets. The engine reads and uses the theme's files to know how the various widgets should be drawn. Some engines come with themes of their own. Each engine has its advantages and disadvantages, and some engines add special properties and features.

Many theme-engines can be obtained from the default repositories. Debian-based Linux distros can execute "apt-get install gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico" to install three different engines. Many engines are available for both GTK2 and GTK3. Below is a small list of examples.

- gtk2-engines-aurora - Aurora GTK2 engine
- gtk2-engines-pixbuf - Pixbuf GTK2 engine
- gtk3-engines-oxygen - Engine port of the Oxygen widget style to GTK
- gtk3-engines-unico - Unico GTK3 engine
- gtk3-engines-xfce - GTK3 engine for Xfce