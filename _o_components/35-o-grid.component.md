---
permalink: /components/grid/
title: "Grid"
comp: grid
---

{% include base_path %}
{% include toc %}

## Introduction
The `o-grid` component is used to display a two-dimensional list view that arranges cells into grid-based layout.

For adding a grid component to your application you must insert the `o-grid` in your page and include a `o-grid-item` component wrapping the desired grid item type you want to display. 

![Grid component]({{ "/images/components/grid/basic-grid.png" | absolute_url }}){: .comp-example-img width='65%'}

## Define title
The `o-grid` component allow to specify a title by setting the value to `title` attribute, this value will appear in the toolbar.

## Show controls
The `o-grid` component show controls by default, you can configure hide the controls with `show-controls=no` property.

## Define columns per row
You can specify a cols per row adding value to the `cols` attribute. By default, the number of columns will be automatically determined based mediaQuery of Flex Layout. See more [here](https://github.com/angular/flex-layout/wiki/Responsive-API#mediaqueries-and-aliases).

The following table shows the default columns that will appear in the grid according to the size of the screen.
<table>
  <thead>
    <tr><th>Breakpoint</th><th>Number columns</th></tr>
  </thead>
  <tbody>
    <tr><td>xs,sm</td><td>1</td></tr>
    <tr><td>md</td><td>2</td></tr>
    <tr><td>lg,xl</td><td>4</td></tr>
  </tbody>
</table>

## Define items per page
 by setting the value to 
The `o-grid` component allows to configure the number of items per page  by setting the value to  `page-size`. By default this value is *32*.

You also configure the set of provided page size options to display to the user with `show-page-size=yes` because by default this selector is hidden. The `o-grid` component allows to configure a array of values to `page-size-options`. By default, the value is *[8, 16, 24, 32, 64]*.

![Grid page size]({{ "/images/components/grid/grid-page-size.png" | absolute_url }}){: .comp-example-img }

```html
 <o-grid #grid columns="id;name;username;email;companyname" keys="id" [static-data]="getStaticData()"
  show-page-size="yes" [page-size]="pageSizeOptions">
    <o-grid-item *ngFor="let list of grid.dataArray">
      <o-column layout-padding class="container-item">
        <img [src]="list.thumbnailUrl" style="margin-top:8px">
        <h4> {% raw %}{{list.name}} {% endraw %}</h4>
        <div class="phone">
          <mat-icon>phone</mat-icon> <span> {% raw %} {{ list.phone }}{% endraw %} </span></div>
        <div class="email">
          <mat-icon>email</mat-icon> <span> {% raw %} {{list.email}} {% endraw %}</span></div>
        <div class="domain">
          <mat-icon>domain</mat-icon> <span> {% raw %} {{list.companyname}} {% endraw %} </span></div>
        <div class="website">
          <mat-icon>website</mat-icon> <span> {% raw %} {{list.website} }{% endraw %} </span></div>
        <div class="body">
          {% raw %} {{list.body}} {% endraw %}
        </div>
      </o-column>
    </o-grid-item>
  </o-grid>
``` 
```
pageSizeOptions =[24,32,64]:

```

## Define sorting
The `o-grid` component allow to sort the grid items adding `orderable='yes'`. You must configure `sortable-columns` with columns of the sorting, separeted by ';'. 

You also can specify the column by which you want it to be ordered when the grid is built by adding the attribute `sort-column`.

![Grid component]({{ "/images/components/grid/grid-sortable_2.png" | absolute_url }}){: .comp-example-img }

```html
<o-grid #grid  columns="id;name;username;email;companyname" keys="id"  [static-data]="getStaticData()"
orderable="yes" quick-filter="yes" sortable-columns="name;email" sort-column="name" grid-item-height="1:2">
  <o-grid-item *ngFor="let list of grid.dataArray">
    <o-column layout-padding  class="container-item">
      <img [src]="list.thumbnailUrl" style="margin-top:8px">
      <h4>{{list.name}}</h4>
      <div class="phone"><mat-icon>phone</mat-icon> <span> {{list.phone}} </span></div>
      <div class="email"><mat-icon>email</mat-icon> <span>{{list.email}} </span></div>
      <div class="domain"><mat-icon>domain</mat-icon> <span> {{list.companyname}} </span></div>
      <div class="website"><mat-icon>website</mat-icon> <span> {{list.website}} </span></div>
      <div class="body">
            {{list.body}}
      </div>
    </o-column>
  </o-grid-item>
</o-grid>
```


## Define grid item height
The height of the rows in a grid list can be set via the `grid-item-height` attribute. By default this value is *1:1*.

- *Fixed height*: The height can be in px, em, or rem. If no units are specified, px units are assumed (e.g. 100px, 5em, 250).
- *Ratio*: This ratio is column-width:row-height, and must be passed in with a colon, not a decimal (e.g. 4:3).
- *Fit*: Setting `grid-item-height`  to fit This mode automatically divides the available height by the number of rows. Please note the height of the o-grid or its container must be set.



## QuickFilter
By default this option is enabled, the filter is visible in the top right. You can be disabled with `quick-filter="no"` property.


## Custom grid item

When building an `o-grid` component you can must your own grid item. For including a custom grid item, **OntimizeWeb** offers the `o-grid-item` directive that can be attached to an angular material grid tile (`mat-grid-tile`) .

```html
<o-grid #grid  columns="id;name;username;email;companyname" keys="id"  [static-data]="getStaticData()"
  orderable="yes" quick-filter="yes" grid-item-height="1:2" sortable-columns="name;email" >
    <o-grid-item *ngFor="let list of grid.dataArray">
      <o-column layout-padding  class="container-item">
        <img [src]="list.thumbnailUrl" style="margin-top:8px">
        <h4>{{list.name}}</h4>
        <div class="phone"><mat-icon>phone</mat-icon> <span> {{list.phone}} </span></div>
        <div class="email"><mat-icon>email</mat-icon> <span>{{list.email}} </span></div>
        <div class="domain"><mat-icon>domain</mat-icon> <span> {{list.companyname}} </span></div>
        <div class="website"><mat-icon>website</mat-icon> <span> {{list.website}} </span></div>
        <div class="body">
              {{list.body}}
        </div>
      </o-column>
    </o-grid-item>
  </o-grid>
```

![Grid item custom]({{ "/images/components/grid/grid-sortable.png" | absolute_url }}){: .comp-example-img}


## Demo

You can see this and more examples of this component in the [OntimizeWeb playground](https://try.imatia.com/ontimizeweb/playground/main/grid/).