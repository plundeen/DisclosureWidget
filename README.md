# DisclosureWidget (a.k.a. Expand/Collapse buttons)

This project contains `XControls` that provide basic ["Disclosure Widget"](https://en.wikipedia.org/wiki/Disclosure_widget) functionality: buttons that can dynamically **expand** and **collapse** the containing front panel by a set number of pixels.

There are two separate `XControls`: one for horizontal expand/collapse behavior, and one for vertical.

# Demo

<details>
    <summary>Demo Gif</summary>
    <img src=img/xcontrol_expand.gif width=100%></img>
    <i>Hey, this is a DisclosureWidget, too!</i>
</details>


# Features

* Right-click on an instance of either `xcontrol` to specify the number of pixels to expand the front panel.
  * Expansion is relative to the `xcontrol` itself, specifically the bottom of the `xcontrol` for the vertical item, and the right side of the control for the horizontal.
  * The specified value is applied as the "Size" property, which is maintained in the local state of the `xcontrol`.
    * This property will persist across unload of the VI from memory, *provided that you save it after making the change*
* By using `xcontrols`, the expand/collapse operations are supported in <u>both runtime *and* edit mode</u>.
  * This makes it easy to adjust the expanded size during development.

# Caveats / Known Issues

* These `xcontrols` don't play nicely with multi-pane front panels, or within subpanels. 
* The `xcontrol` will attempt an intial resize when the owning VI is first loaded; this is typically desired, but could be surprising if unexpected.
 * It is advised that you configure the "Size" property and save calling VIs in the desired state such that there is no immediate resizing on VI load.
* The `xcontrols` do not currently support setting the default value (always initialize collapsed)
* Repositioning the `xcontrol` does not immediately autosize.
  * You will need to toggle the button to re-adjust the size after you move the control.
