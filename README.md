# sorting-notes

(created August 15, 2021 and September 16, 2021; first published June 11, 2023)

sorting-notes is a Python script that creates a sortable HTML table of all the files in a directory. The table can be sorted by name, date modified, file size, and time modified.

## Usage

When run, sorting-notes will create an HTML file named based on the current time. For example: `sorting-notes-202603301206.html`.

sorting-notes will, by default, generate a table for all the files in the directory you place it in. You may change the search_dir variable in line 5 to list the files in another directory. For instance, changing it to `"Documents/"` will generate a listing for the Documents directory located inside the one you are currently working in. Make sure to include the trailing slash!

You may also change `title` in line 8 to change the title of the page sorting-notes generates. The default is `the notes folder`.

sorting-notes is built to work with Stuart Langridge’s [sorttable](https://www.kryogenix.org/code/browser/sorttable/) JavaScript library. [Download a copy of sorttable](https://www.kryogenix.org/code/browser/sorttable/sorttable.js) and place it in the same directory as the file sorting-notes generated in order to enable sorting. Click a heading to sort by that data point; click it again to sort the other direction.

## Rudimentary time zone support

If some of your notes were saved outside of your home time zone, you can modify tzbreaks and tzoffset (on lines 4 and 5) to account for this.

Suppose I live in New York and traveled to Paris in September 2023 — let’s say I arrived on September 1 and returned on September 15. I was in transit at 12 AM New York time on September 1, and at 12 PM New York time on September 15.

I would add `1693540800` and `1694793600` to my tzbreaks list, and `6` and `0` to my tzoffset list. 

The lists should look like this:

`tzbreaks = [0, 1693540800, 1694793600, 9999999999]`

`tzoffset = [0, 6, 0, 0]`

The way this works: starting at 1693540800 (12 AM Sep 1 2023 in New York), the timestamps of my notes will be displayed in Paris local time, which is 6 hours ahead of my home time zone. Then, starting at 1694793600 (12 PM on Sep 15), they will be displayed in New York time again.

Ensure that tzbreaks is sorted chronologically, and the indices of tzoffset align with those of tzbreaks - otherwise, it might not work correctly!

## [Example output](https://jmoll1125.github.io/sorting-notes/demo/)
## [Download sorting-notes](https://jmoll1125.github.io/sorting-notes/sorting-notes.py)
