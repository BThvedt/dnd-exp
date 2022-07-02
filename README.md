How the json works

It can be done in one of two ways. You can have an 'editable_components' array defined, with a semi-rigid structure, or you can use special keys that start with d\_ to define the structure.

The items are arranged into sections, areas, and zones. A zone can contain one or more areas, and an area can contain one or more sections. Each sections can define on it's own if things can be added, removed, or sorted, and what can be dropped into it.

When defining a structure, the type can be 'area', 'section' or 'zone', but no matter what, it always gets formatted into the sayme type of structure:

    {
    		areas: [
    				{
    						sections: [
    								{
    										items: [
    											{item}
    										]
    								}
    						]
    				}
    		]
    }

The 'zone' is the root level. Whichever root level is defined, it always gets formatted this way, and each 'zone', area, section, and item will get a unique id that will look like this z1a1 (for an area) or z2s3a2i4 (for an item).. etc.

When defining the structure, you need a title and type at the root level. Wheter or not you break it up into area, sections, is up to you, but there has to be "items" each of which represent some kind of component in that page.

When defining a zone, stray items get put into their own area. When defining an area, stray items get put into their own section. Sections and areas can have their own

There are some special classes 'single_area', 'multiple_sections' etc that are added - just for styling. And although the root level json is always a 'zone', it retains the 'type' that was defined (again, might be useful for styling i dunno, might change that later)

Although defining an 'editable\*components' section is easier to understand, it's not convienent in actual practice. So in practice, I prefer to define things with the d\_ keys in the JSON

to define an area use a d_type: zone or d_type: area (or section) and a d_name: (a unique name), a d_title if the root, and a d_parent if a subsection. Items only need a d_parent.

Then the code refactors the json on the front end into the editable_components structure, (alternate ids might be needed, save that for later) and then goes from there.
