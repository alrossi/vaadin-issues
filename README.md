# \<vaadin-issues\>

The component included here is extracted and simplified into a standalone from
a larger frontend administrative interface for the dCache project
(https://github.com/dCache).

The purpose of the demo is to illustrate two issues in Firefox:

1.  very slow rendering of this particular template in comparison 
    to other browsers;
2.  general jitteriness when scrolling the vaadin-grid rows.

Data is added to the table from a hard-coded window variable.  Note
that the problems encountered above are independent of the data
load time.  

dCache's "dcache-view" uses the vaadin-grid components extensively, both
with and without remote lazy-loading data providers.  Whether
the data is loaded all at once or by using paging, the same performance
disparity is observable between Safari / Chrome on the one hand (which
work perfectly well), and Firefox on the other.

## Checkout and build

After checking out the code, be sure to run

```
$ bower install
```

in order to download the necessary dependencies.

## Install the Polymer-CLI

First, make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.

## Viewing Your Element

```
$ polymer serve
```

Use the indicated URL ( http://127.0.0.1:8081/components/vaadin-issues, 
redirected to /demo) to observe these problems.   Try
to load the page in Safari and Chrome, and then in Firefox.

With Firefox, you should observe the behaviors indicated by the screenshots
included in the repository. 

1.  firefox-delay.png       shows the stalled rendering.
2.  firefox-scrolling.png   after stopping the stalled rendering (above),
                            this is the result, which also shows scrambled 
                            columns and empty rows when you scroll.
                            (NOTE:  this is a problem we have encountered with
                            vaadin-grid scrolling in Firefox even
                            when there is no redering delay).
3.  chrome.png              is for comparison purposes (normal behavior).

