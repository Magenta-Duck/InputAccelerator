Requirements
============

## Overview

When inputting data into web sites/apps, henceforth referred to as 'site(s)', very frequently, for example when scanning barcodes to triarge/value donations, often the site isn't designed with speed in mind and becomes a significant obstacle.

When we're talking about processing 100+ items an hour, even minor improvements to the speed of input can lead to significant improvements in results because of the scale involved - not just on an individual level but across an organisation too.

We therefore need a Chrome extension that will alter specific web sites/apps to accelerate how quickly we can use them.

## Use Cases

### Searching by Barcode

A user has a stack of items with barcodes that they wish to value on a website like Amazon.  The current process is:

1. Click in the search box with the mouse.
1. Scan the item's barcode.
1. Scroll down the page evaluating the results.
1. Maybe click on the item to get further details.
1. Value the item.
1. Scroll back to the top of the page.
1. Double-click the search box to select all the content.
1. Go to 2.

The times where the user is reaching for the mouse to do something precise (click in the search box, select all the content, scroll to the top of the page, etc.) all slow down the process.  This is especially true when you're quickly evaluating hundreds of items, where you just want to "yes or no" each.

Instead we'd like the process to be as follows:

1. Scan the item's barcode.
1. Scroll down the page evaluating the results.
1. Maybe click on the item to get further details.
1. Value the item.
1. Go to 1.

This process requires that the search box always be automatically focussed and all content within it selected, but then means that interaction with the mouse is minimal or eleminated completely (using Page Down) and frees up the user's hands to be handling items and scanning them much more quickly.

### Selecting Item Condition Drop-down

When listing an item for sale online, often you need to choose a condition from a drop-down menu, e.g. "Like New", "Very Good", "Good", etc.  Often this field is within a large form containing many fields, most of which you don't want to change as they're pre-populated with information from the tool's database.

The current process is:

1. Scroll down the form to until you see the condition drop-down.
1. Click the drop-down to bring up the options.
1. Click the option you want.

First, a sane default value should be set so that in most cases it would completely eliminate the need to find and use the field at all.  For example "Very Good" is by far the most common (as condition is a key factor when selecting items for listing online).

If the condition does need to be altered from its default, two processes should be available..

First, the drop-down is replaced with a [segmented button](https://m3.material.io/components/segmented-buttons/overview) such that the process becomes:

1. Scroll down the form until you see the condition segemented button.
2. Click the condition you want.

A further optimization would be to add keyboard shortcuts for the different conditions, e.g. Alt + L = "Like New", Alt + G = "Good", then the process would become:

1. At any point, press the shortcut for the condition you want, e.g. Alt + G.

## Accelerations

### Text Field Focus and Selection

Focus the specified field and select all the content within such that it's overwritten when any content is input.

### Default Values

Set a default value for a field, the field could be any HTML input.

### Tab Index Injection

Set the tab index of a field to the specified value.

Having the option to be able to clear all other tab indexes could be very handy such that we can make it really easy to jump to just the fields we need.

### Drop-Down to Segmented Button

Replacing drop-downs with segmented buttons makes them easier to use.

Option to replace all drop-downs on a page like this, optionally with a limit to the number (or text length) of the options - e.g. 5 or less options, turn into segmented button.

### Keyboard Shortcuts

#### Drop Downs

Assign specific keyboard shortcuts to specific options in drop-downs, as discussed in the "Selecting Item Condition Drop-down" use case above.

#### Actions

Assign shortcuts to specific actions within a page (e.g. a Next or Search button).

#### Links

Being able to dynamically assign shortcuts to links following a pattern could be very handy.  For example, mapping Alt + 1, Alt + 2, etc. to the first, second, etc. results of a search.

### Pin Fields

Bring certain fields to either the top of the page, or perhaps in a fixed collapsable overlay.  These pinned fields could then use all of the other acceleration features above.

The idea being that in some cases almost all the fields on a form are pre-populated, so you can bring the most commonly changed ones to the top to speed up input and visibility of those fields.

## Triggers

We'll need various options for when the accelerations are triggered - as, for example, a Single Page Application (SPA) may never reload the page like a traditional site, and needs to be triggered off some other event.

Triggering events could include:

* Page Load
* Pushing \<Enter\> in the field.
* When the field has been cleared.
* When a keyboard shortcut is pressed.

There could be more ways to accommodate specific sites, therefore this system needs to be designed to be flexible.

## Configuration

### Flexibility

We need the extension to be, as much as possible, flexible and be able to be configured by the user to work on any site.

There may be sites that need specific code to deal with, for example Amazon's modal on-focus for search, but where possible they should be solved for the general case and then configured for the specific case so that they can be re-used.

### Rules

The user should be able to setup a set of rules which define which sites are affected, which triggers are used, and which accelerators to employ along with their configuration.

### Enterprise

We'll need the ability for an organisation to be able to define the configuration across thousands of installations and to have updates to configurations rolled out.