# shady-dom-specificity
Demonstrates issues with Polymer 1.0 Shady DOM document style affecting custome elements' Local DOM

## Run the demo

Clone and start polyserve:

    git clone https://github.com/brianreeve/shady-dom-specificity.git
    cd shady-dom-specificity
    polyserve -p 85

Then in a browser:

    [http://localhost:85/components/shady-dom-specificity/demo/index.html](http://localhost:85/components/shady-dom-specificity/demo/index.html)

The text should be big and green, but you'll see the document styles take over the element's styles when using Shady DOM.

If you inspect the element you'll see that the Shady DOM shim causes the document styling to have higher specificity. As it appears on top of the Local DOM styling in the Styles stack:

    ul:not([style-scope]):not(.style-scope), p:not([style-scope]):not(.style-scope) {
    	font-size: 12px;
    	color: red;
    }

    .container.x-menu ul, .container.x-menu p {
    	font-size: 30px;
    	color: green;
    }

In Chrome, you can force native Shadow DOM and it works as intended:

    [http://localhost:85/components/shady-dom-specificity/demo/index.html?dom=shadow](http://localhost:85/components/shady-dom-specificity/demo/index.html?dom=shadow)