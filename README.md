# Virtual Parents

A module for ProcessWire CMS/CMF. Allows pages in Page List to be grouped under a virtual parent.

This module manipulates the page list and the flyout tree menu to make it appear that one or more pages are children of another page when in fact they are siblings of that page.

Why would you do that instead of actually putting the child pages inside the parent? Mainly if you want to avoid adding the parent name as part of the URL. For example, suppose you have some pages that you want to be accessed at URLs directly off the site root: yourdomain.com/some-page/. But in the page list you want them to be appear under a parent for the sake of visual grouping or to declutter the page list under Home.

#####Example of how the page structure actually is

![Before](https://user-images.githubusercontent.com/1538852/31802366-53b79a16-b5aa-11e7-8b6a-8bd2e1361b87.png)

#####Example of how the page structure appears with Virtual Parents activated
![After](https://user-images.githubusercontent.com/1538852/31802365-53858c4c-b5aa-11e7-91c2-ea145baa9349.png)

## How it works

This module identifies the virtual parents and virtual children by way of template. You define a single template as the virtual parent template and one or more templates as the virtual child templates. Anytime pages using the child template(s) are siblings of a page using the parent template, those child pages will appear as children of the virtual parent in the page list and tree menu.

You will want to create dedicated templates for identifying virtual parents and virtual children and reserve them just for use with this module.

## Features

* Adjusts both page list and tree flyout menu to show the virtual parent/child structure, including the count of child pages.
* Works everywhere page list is used: Page List Select / Page List Select Multiple (and therefore CKEditor link dialog).
* Intercepts the "Add page" process in admin, so that when an attempt is made to add a child to a virtual parent, the child is added where it belongs (the next level up) and the template selection is limited to virtual child templates.
* Intercepts moving and sorting pages in the page list, to ensure only virtual children may be moved/sorted under the virtual parent.
* Superusers have a toggle switch at the bottom of the page list to easily disable/enable Virtual Parents in order to get a view of what the real page structure is.


## Usage

[Install](http://modules.processwire.com/install-uninstall/) the Virtual Parents module.

In the module config, enter pairs of parent/child template names in the form virtual_parent_template=virtual_child_template. If needed you can specify multiple pipe-separated *child* templates: virtual_parent_template=child_template_1|child_template_2. One pair of template names per line.

There is a checkbox in the module config to toggle Virtual Pages on and off, but it's more convenient to use this from the page list.

## Notes

It's important to keep in mind the real location of the virtual child pages. This module is only concerned with adjusting the appearance of page list and tree menu for the sake of visual grouping and tidiness. In all other respects the virtual children are not children of the virtual parent at all.

It's recommended to select an icon for the virtual parent template (Advanced tab) so virtual parents are marked out in the page list as being different from normal parent pages.

Do not place real children under a virtual parent. There is some protection against this when moving pages in the page list, but when it comes to changing a page's parent via the Settings tab the only protection is common sense.
