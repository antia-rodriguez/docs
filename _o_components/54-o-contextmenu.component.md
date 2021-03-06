---
permalink: /components/contextmenu/
title: "Context menu"
comp: contextmenu
---

{% include base_path %}
{% include toc %}

The **OntimizeWeb** context menu is compound of the `o-context-menu` component and the `oContextMenuData` directive which is attached to a DOM element in which the context menu component appears.

For including the context menu in your application follow the next steps:

* Include the `o-context-menu` component in the template where the context menu will appear. Add as many [`o-context-menu-item`](#context-menu-item){:target='_blank'} components to the context menu as you desire.
* Add the `oContextMenu` directive to the DOM element where the context menu will appear upon user right click and pass a referente to the previously defined `o-context-menu` component.

## Context menu item

The `o-context-menu-item` component represents each item of the context menu component.

In some cases you may need context information when executing the action triggered by the `o-context-menu-item`, use the [`oContextMenuData`](#context-menu-data) directive in the `oContextMenu` host element in order emit it in the `execute` event of the context menu items. Check the **API** section of this page for more information.

## Context menu data

The `oContextMenuData` is an attribute of the `oContextMenu` directive is used for propagating context information when the context menu item is activated or for modifiying the menu item status when this depends on that context information.

## Example

```html
<div [oContextMenu]="myContextMenu" [oContextMenuData]="customData">
  <span>Right click me!</span>
</div>

<o-context-menu #myContextMenu>
  <o-context-menu-item icon="face" label="Item 1" (execute)="onExecute($event)"></o-context-menu-item>
  <o-context-menu-item icon="start_rate" label="Item 2" enabled="no"></o-context-menu-item>
  <o-context-menu-item label="Item 3" [visible]="getVisible" (execute)="onExecute($event)"></o-context-menu-item>
</o-context-menu>
```

```javascript
  onExecute(customData: any) {
    /*
      do whatever you want
    */
  }

  getVisible(data: any): boolean {
    return true;
  }

```

You can see a live example of this component in the [OntimizeWeb playground](https://try.imatia.com/ontimizeweb/playground/main/contextmenu){:target="_blank"}.
