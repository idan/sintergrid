The Sinter Grid System
======================

Sinter is a minimalist, responsive fixed grid system for 
[Compass](http://compass-style.org/).

It _does not_ represent much new thinking; Sinter is a synthesis of various bits I liked from several different grid systems, both in terms of their structure and the Compass implementation. They are, in no particular order:

* [Less Framework](http://lessframework.com/) and its [compass plugin](https://github.com/willhw/compass-less-plugin)
* [960 Grid System](http://960.gs) and its [compass plugin](https://github.com/chriseppstein/compass-960-plugin)
* [Susy](https://github.com/ericam/compass-susy-plugin/)

If you've used any of the above, Sinter's lineage will be obvious.

Sinter is a framework for usage with Compass. There are no plans for creating a standalone CSS version.


The Grid
========

My original impetus was a desire for various screen layouts to be divisible by three and four. Less provides a fantastic breakdown of media queries, but I was unhappy with the column layouts.

Sinter is based on 960's 12-column grid. It consists of *60-pixel columns* with *20-pixel gutters*. Like 960, the gutters are evenly distributed on either side of the column, meaning that each column has 10 pixels of padding on either side.

Here are the various device layouts:

* 320px (portrait iPhones): four columns, 300px wide, with 10px padding for the grid container.
* 480px (landscape iPhones): 6 columns, 460px wide, 10px padding.
* 768px (portrait iPads): 9 columns, 700px wide, 34px padding.
* 960px (default layout): 12 columns, 940px wide, 10px padding.
* 1200px (wide desktop): 15 columns, 1180px wide, 10px padding.
* 1280px (720p HD): 16 columns: 1260px wide, 10px padding.

Every layout is divisible by two, three, or four. The most significant wart in this system is the padding on the 768px layout.

What doesn't it do?
===================

Sinter does not supply any form of CSS reset. Compass provides several great mixins for that purpose.

Anything relating to typography is unhandled by the framework. Compass provides some great facilities for vertical motion in type, there's no need to duplicate that work in the grid system.


What other cool features does it have?
======================================

Honestly, read the source. There's really not much there.

Some stuff I liked and wrote or cherry-picked:

* Sass functions for computing column widths for when you need to add padding or a border to some element, as well as a specialized variant for input fields.
* A background grid mixin, which utilizes Compass's [built-in CSS3 grid generator](http://compass-style.org/reference/compass/layout/grid_background/): `sinter-grid-background($columns)`.
* A mixin for automatically setting a contrasting selection color given a text color: `accessible-selection-color($color)`.


How do I use it?
================

In the future, this will probably become a proper Compass plugin. For now, the usage is ghetto-stupid: copy the following to wherever you put your Sass files:

* The `sinter` directory
* The `partials` directory
* `screen.scss`

Avail yourself of the source until some proper documentation can be written.


Quick overview
==============

Available mixins
----------------

* `grid($cols)`: the complete grid itself, centered
* `columns($cols)`: number of columns for the element
* `prefix($cols)`: blank columns before the element
* `suffix($cols)`: blank columns after the element
* `pad($cols)`: blank columns on each side of the element
* `alpha`: no left gutter
* `omega`: no right gutter
* `full($cols, $pad)`: utility mixin
* `sinter-grid-background($cols)`: display the grid itself (for debugging purposes)
* `accessible-selection-color($color)`: get a contrasting color

Sample
------

Here's an example usage for a blog layout:

                   ------++------++------++------++------++------++------++------++------++------++------++------
                                   +------------------------------------------------------------+
             full(8,2)------------>|                                                            |
                                   |                        SINTER  DEMO                        |
                                   |                                                            |
            columns(6)-------------------+                                               +---------------columns(2)
            alpha                  |     v                                               v      |        omega
                                   +--------------------------------------------+  +------------+
                                   |Nav 1   Nav 2   Nav 3   Nav 4   Nav 5       |  |       Login|
                                   +--------------------------------------------+  +------------+
                                   |                                                            |
                                   |                                                            |
                                   +------------------------------------------------------------+
                   +------------+---------------------------------------------------------------+  +------------+
                   | MetaData   |  . Blog post title                                            |  | Sidebar    |
                   |            |  .                                                            |  |            |
                   |  Author    |  . some content                                               |  |   tag1     |
      columns(2)-->|  Date      |  .                                                            |  |   tag2     |
      alpha        |  Category  |  .                                                            |  |   tag3     |
      omega        |  Tags      |  .                                                            |  |   tag4     |
                   +------------+  .                                                            |  |   tag5     |
                   |               .                                                            |  |            |
                   |               .                columns(10)                                 |  | Blogroll   |
                   |               .                alpha                                       |  |   stuff    |
                   |               .<---------------------------------------------------------->|  |   foo      |
                   |               .                                                            |  +------------+
                   |  prefix(2)    .                                                            |         ^
                   |<------------->.                                                            |         |
                   |               .                                                            |         |
                   +----------------------------------------------------------------------------+         |
                                                                                                      columns(2)
                                                                                                      omega
                   
                   
                                           +--------------------------------------------+
                           full(6,3)------>| Footer, Copyright, stuff                   |
                                           +--------------------------------------------+
                   ------++------++------++------++------++------++------++------++------++------++------++------

Legend:

* one char represents 10 pixels
* +------+ represents 10px gutter, 60px column, 10px gutter

What browsers are supported?
============================

I haven't tested anything yet. There's a fix for the IE6 double-margin bug which you can strip out of the columns mixin, but it has no negative effects on other browsers.


License?
========

Short answer: BSD. Long answer: this reuses code from all over, so check out `LICENSE.txt`.


Contributors & Thanks
=====================

Sinter was... sintered together by Idan Gazit / @idangazit.

No kidding, Sinter is 99% theirs and 1% mine. Thanks to:

* Joni Korpi / @jonikorpi
* William Wells / @williamhanwells
* Nathan Smith / @nathansmith
* Chris Eppstein / @chriseppstein
* Eric A. Meyer / @eriiicam
