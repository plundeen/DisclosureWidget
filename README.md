# DisclosureWidget (a.k.a. Expand/Collapse buttons)

This project contains `XControls` that provide basic ["Disclosure Widget"](https://en.wikipedia.org/wiki/Disclosure_widget) functionality: buttons that can dynamically **expand** and **collapse** the containing front panel by a set number of pixels.

There are two separate `XControls`: one for horizontal expand/collapse behavior, and one for vertical.

# Features / Usage

<details>
    <summary>Demo gif</summary>
    <img src=img/xcontrol_expand.gif width=100%></img>
    <br>
    <i>Hey, this is a DisclosureWidget, too!</i>
    <br>
</details>


* Right-click on an instance of either `xcontrol` to specify the number of pixels to expand the front panel.
  * Expansion is relative to the `xcontrol` itself, specifically the bottom of the `xcontrol` for the vertical item, and the right side of the control for the horizontal.
  * The specified value is applied as the "Size" property, which is maintained in the local state of the `xcontrol`.
    * This property will persist across unload of the VI from memory, *provided that you save it after making the change*
* By using `xcontrols`, the expand/collapse operations are supported in <u>both runtime *and* edit mode</u>.
  * This makes it easy to adjust the expanded size during development.
* Notice that there is <u>no code needed on the block diagram</u>?

# Caveats / Known Issues

* These `xcontrols` don't play nicely with multi-pane front panels, or within subpanels. 
* The `xcontrol` will attempt an intial resize when the owning VI is first loaded; this is typically desired, but could be surprising if unexpected.
 * It is advised that you configure the "Size" property and save calling VIs in the desired state such that there is no immediate resizing on VI load.
* The `xcontrols` do not currently support setting the default value (always initialize collapsed)
* Repositioning the `xcontrol` does not immediately autosize.
  * You will need to toggle the button to re-adjust the size after you move the control.
* This is an `xcontrol`, so all the usual caveats apply:
  * Troubleshooting is a bit cumbersome, but you *can* right click and select `Advanced > Show Diagram` to view/probe the block diagrame of the facade.
  * All the `xcontrol` library files will be `reserved` as long as there are an VIs in memory with an instance of the `xcontrol` on its front panel.
  * See also: [debugging xcontrols](https://zone.ni.com/reference/en-XX/help/371361R-01/lvhowto/debugging_xcontrols/)