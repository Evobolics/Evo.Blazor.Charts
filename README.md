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
