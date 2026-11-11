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
