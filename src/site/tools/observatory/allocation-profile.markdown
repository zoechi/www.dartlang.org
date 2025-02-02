---
layout: default
title: "Allocation Profile"
description: "Observatory's Allocation Profile feature lets you examine memory use in old space and new space in your Dart application."
header:
  css: ["observatory.css"]
---

{% include breadcrumbs.html %}

# {{ page.title }}

<h4>Contents</h4>
<ol class="toc">
  <li> <a href="#allocation-statistics">Allocation statistics</a> </li>
  <li> <a href="#allocation-table">Allocation table</a> </li>
</ol>

Dynamically allocated Dart objects live in a portion of memory
called the [_heap_](glossary.html#heap). Typically, when an object
is first allocated, it is created in the part of the heap known as 
[_new space_](glossary.html#new-space). This area is ideally suited
for objects that are smaller and short-lived, such as local variables.
Garbage collection (GC) is performed frequently in new space.

Longer lived objects that survive garbage collection in new space are 
promoted to [_old space_](glossary.html#old-space). Old space is larger
than new space and is well suited for larger objects or objects that
are longer lived.

Observatory's Allocation Profile screen lets you peek at how an
isolate is using memory at a given moment.  This screen also provides
_accumulator_ values that you can use to study the rate of memory allocation.
The accumulators are useful if you suspect that your application is
[leaking memory](glossary.html#memory-leak), or has other bugs
relating to memory allocation.

Next to Refresh, the blue bar at the top of the
Allocation Profile screen has two additional buttons:

<img src="images/AccumulatorButtons.png" alt="Buttons specific to the Accumulator Profile screen">

GC
: Initiates a garbage collection pass for both old space and new space
  and refreshes the displayed data.

Reset Accumulator
: Zeroes out the Accumulator columns in the allocation table and
  refreshes the displayed data.

You can use the Refresh button,
at any time, to update the sample. Memory usage is volatile,
and these graphs can change dramatically from sample to sample.

## Allocation statistics {#allocation-statistics}

At the top of the Allocation Profile screen, two pie charts, along with some
statistics, provide a high-level glimpse into new space and old space.

The following screenshot shows the activity in new space for a root isolate:

<img src="images/NewSpacePieChart.png" alt="Pie chart showing usage of new space">

At the time of the sample, 67.8% of new space is used and the garbage collector
has passed over new space 598 times, requiring a total of 1.26 seconds of
CPU time. The following screenshot shows the activity of old space,
sampled at the same moment:

<img src="images/OldSpacePieChart.png" alt="Pie chart showing usage of old space">

The data shows that old space is 90% used. Also, garbage collection
has been performed once in the same amount of time that new space
has been garbage collected 598 times. An average GC cycle for new space
requires 2.11 milliseconds compared to 14.84 milliseconds for a
single pass over old space.
Because old space is much larger than new space, it is unsurprising that 
garbage collection of old space requires more time.

## Allocation table {#allocation-table}

The table below the pie charts contains detailed information about
allocated objects, aggregated by class.

<img src="images/AllocatedMemoryList.png" alt="List of objects allocated and in old space">

Note that four columns list Accumulator information and 
four columns list Current information.

The Accumulator columns contain information about objects since
the beginning of the isolate's execution or since the reset accumulator
button was last clicked, whichever is most recent.

The Current columns contain information about objects that
have survived the last garbage collection cycle as well as new objects that
have been allocated since the last GC cycle. If any of the recently
allocated objects have become garbage, they are still counted until
the next garbage collection.

The information in the Accumulator columns is under your control&mdash;
when you click the **Reset Accumulator** button, the
accumulator columns in the table are set to 0. You can get your app
to a particular state, then pause it and reset the accumulator.
Resume the program, and refresh the table. You can now see if the
memory allocated in that interval is what you expected.

You can affect the information in the Current columns by
clicking the **GC** button to force a garbage collection cycle.

The columns in the table are as follows:

Class
: An aggregate of the objects allocated to this class.
  Clicking the class name takes you to a class evaluation
  screen where you can enter Dart code to query the class.
  For more information, see [Evaluating Expressions](evaluate.html).

Accumulator Size (New)
: Total amount of memory used in new space since last accumulator reset.

Accumulator (New)
: Total number of objects in new space since last accumulator reset.

Current Size (New)
: Total amount of memory used by current objects in new space.

Current (New)
: Total number of current objects in new space.

Accumulator Size (Old)
: Total amount of memory used in old space since last accumulator reset.

Accumulator (Old)
: Total number of objects in old space since last accumulator reset.

Current Size (Old)
: Total amount of memory used by current objects in old space.

Current (Old)
: Total number of current objects in old space.

By default, the table is sorted by the Accumulator Size (New) column,
from largest value to smallest,
but you can click any column name to sort the data on that column.

---

{% include observatory_new_fyi.html %}

{% include observatory_footer.html %}

