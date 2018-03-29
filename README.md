# \<vaadin-provider-with-filters\>

The component included here is adapted from jsbin.zoziget.3.html
(https://jsbin.com/laxuxah/edit?html,output).

The purpose of the demo is to illustrate the fact that when you
attache a data provider function using connected callback,
the function is called each time a column filter is initialized.

While nothing serious happens using IronAjax (as per your demo
boilerplate), this behavior does lead to a corrupted data cache 
if the provider is using asynchronous lazy loading with paging (see below). 

Note that the filters are (of course) unimplemented in this snippet,
but this is irrelevant to the point being illustrated.

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

Use the indicated URL (http://127.0.0.1:8081/components/vaadin-provider-with-filters/, 
redirected to /demo) to observe these problems.   The console logging
should reveal the multiple calls.


## Lazy loaded RESTful data

I am not sure how to use the URL providing demo data to do offset+limit, so I
have included the decorator component I have written to handle all the provider 
functionality for our framework.  This is for inspection only, as it is
missing a couple of mixin dependencies.

If you examine the runProvider function, you will see what I mean.  Without

```
    if (params.filters.length !== this.numberOfFilters) {
        return;
    }
```

the data cache gets corrupted.
