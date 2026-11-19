# Frequently Asked Questions

### How do I find the CSS selector for a GTK widget?

GTK Inspector shows the widget and CSS-node trees; it does not provide a ready-to-copy selector. Build a selector from the CSS node names, style classes, and widget names shown there.

1. Open Inspector in the application with `Ctrl`+`Shift`+`I` (or `Ctrl`+`Shift`+`D`). You can also start the application with `GTK_DEBUG=interactive application-name`.
2. Use the Inspector's picker to click the exact part of the interface you want to change.
3. In the Objects view, expand **CSS Nodes** and follow the tree to the node that draws that part. Check its name and any style classes. Also check its parents: the padding may belong to a surrounding button or container rather than the text label itself.
4. Turn the node path into a GTK selector and try a narrow rule in the Inspector's CSS view. Once it matches, put it in your theme's `gtk.css` and restart the application to confirm it.

For example, if the CSS-node tree for a path bar actually shows `pathbar > button > label`, this selector targets the label directly inside a button in that path bar:

```css
pathbar > button > label {
  padding: 0;
}
```

That path is only an example: applications and GTK versions can use different node names and classes. Use the names shown for your application. In GTK selectors, node names are written as elements (`label`), style classes get a leading dot (`label.dim-label`), and widget names get a `#` (`label#breadcrumb`). A space matches a descendant; `>` matches a direct child. Start with the shortest selector that targets only the intended part, rather than styling every `label` in the
 application.

See the GTK documentation for [running GTK Inspector](https://docs.gtk.org/gtk3/running.html) and [GTK CSS nodes and selectors](https://docs.gtk.org/gtk3/css-overview.html).

### How do I find the class names of a GTK widget?

1. Open GTK Inspector with `Ctrl`+`Shift`+`I` or `Ctrl`+`Shift`+`D`.
2. Use the picker to select the widget.
3. In the Objects view, open **CSS Nodes**.
4. Expand the hierarchy and read the node name and style classes. A class is available only if the widget exposes it in this tree.

### How do I add borders to GTK 3 notebook tabs?

`GtkNotebook` exposes a `notebook > header > tabs > tab` CSS-node hierarchy. The header has a position class such as `.top` or `.bottom`, and the selected tab matches `:checked`. Confirm the actual tree in GTK Inspector, since the application and tab position can change the selector.

For tabs above the page, this GTK 3 rule adds a border to each tab and gives the selected tab a darker border:

```css
notebook > header.top > tabs > tab {
  border: 1px solid #777;
}

notebook > header.top > tabs > tab:checked {
  border-color: #333;
}
```

For tabs below the page, change `header.top` to `header.bottom`. Use `header.left` or `header.right` for vertical tabs. The `GtkNotebook:show-border` setting controls the page frame; it is separate from borders on the tabs.

To make sure the rule works outside Inspector:

1. Try it in Inspector's **CSS** tab. Inspector CSS edits are temporary and are lost when the application exits.
2. Put the working rule in `~/.config/gtk-3.0/gtk.css` (or `$XDG_CONFIG_HOME/gtk-3.0/gtk.css`).
3. Fully quit and relaunch the application so GTK loads the user stylesheet.
4. If it still differs, compare the application's GTK version and theme, and check Inspector's CSS tab for the loaded providers and any more-specific rule overriding yours.

This applies to GTK 3. GTK 4 uses a different user stylesheet location. See the [GtkNotebook CSS nodes](https://docs.gtk.org/gtk3/class.Notebook.html#css-nodes) and [GTK CSS overview](https://docs.gtk.org/gtk3/css-overview.html).
