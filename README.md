# Evo.Blazor.Charts
A blazor Chart Library

# Research

* https://jack-kelly.com/html5_canvas_versus_svg_for_interactive_charts_and_graphical
* https://css-tricks.com/when-to-use-svg-vs-when-to-use-canvas/

## Objectives

* Be able render the canvas blazor object within the chart
* Be able to draw an SVG on top of the canvas using another z-layer (possibly)

## 5/23/2021 - Draw an SVG and Canvas

By default the SVG is placed down below the the canvas, not on top of it.  Going to correct this using some z-layers, realtive positioning, and negative top.

Need to figure out how to get the negative top.

Figured it out:

```
@using Evo.Services.Blazor;
@namespace Evo.Components.Blazor
@inherits EvoUIComponentBase<ChartService_I>
@*Check to see if the control is visible.  *@
@if (IsVisible)
{
    @* Allows for child components to discover their parent, reference it, and register with it.*@
    <CascadingValue Value="@this">
        @ChildContent
    </CascadingValue>
    <!-- The div does nothing to affect the stretching of the canvas within a splitter. Setting
        the height, width and overflow to hidden gets rid of the scrollbar.  The content of the 
        svg and the canvas intially takes up too much space vertically when measuring the flow layout.
        Settting the width and height, keeps the bounding box to the dimensions we want, and the 
        overflow trims reserved content area that will not be used. -->
    <div chart style="height:@Height;width:@Width;overflow:hidden;">
        <EvoCanvas></EvoCanvas>
        <!-- By default, the svg is placed below the canvas, not on top of the canvas.-->
        <svg style="position: relative;left:@GetLeft();top:@GetTop();z-index:@ZIndex;height:@Height;width:@Width">
            <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
        </svg>
    </div>
}
```
## Scrolling Chart

http://jsfiddle.net/agconti/k9CFu/

## SVG Charts

* https://observablehq.com/@d3/line-chart
* https://observablehq.com/@d3/candlestick-chart
* https://bl.ocks.org/tompiler/6045b80d2164077faaf96e0304531bba (Zoomable)

## Type Parameters for Databinding
* https://stackoverflow.com/questions/60393496/c-sharp-blazor-how-to-use-typeparam-in-code-behind-with-workaround
* https://blazor-university.com/templating-components-with-renderfragements/using-typeparam-to-create-generic-components/

