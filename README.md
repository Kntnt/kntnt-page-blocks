# Kntnt Page Blocks

*Page Blocks* is a HTML and CSS solution to vertically divide whole or parts of a web page into *blocks* of content.

## Terminilogy and description

A *blocks container* is an element containing all blocks. An element is declared to be a blocks-container by adding the class `blocks`.

A *block* is an element that form a vertical building block inside blocks-container. Blocks follow on each other along an y-axis pointing downwards in the viewport plane. Blocks typically follows on each other, possible with spacer between (see below). An element is declared to be a block by addig the class `block`.

A *spacer* is the HTML element `<hr>` with the class `spacer`. It form a transparent vertical building block inside blocks-container. The amount of vertical space it occupies is determiend by the custom property `--blocks-spacer-height`. It is used to create space between blocks. It is typically used between block of narrow width (see below).

A *part* is an element that form a horizontal building block inside a block. Parts follow on each other along an x-axis pointing rightwards in the viewport plane. An element is declared to be a block by addig the class `part`.

A *layer* is an element that form a layer building block inside a part. Layers follow on each other along an z-axis pointing pointing outwards from the viewport plane. An element is declared to be a layer by addig the class `layer`. Each layer must consists of exactly one element.

A *background layer* is the layer remotest to the reader. In HTML source order, that is the first layer in a part. Currently, background layeras are only used for background images, which should be represented by a single `<img>`-element inside the background layer element. The height of the image affects the height of the block. If necessary to cover the entire layer, the image is zoomed in towards the center. A part can have zero or one background layers. An element is declared to be a background layer by addig the class `bg`.

A *foreground layer* is the layer closests to the reader. In HTML source order, that is the last layer in a part. There is padding around the conent of a foreground layer. The padding is determined by the custim `--blocks-fg-padding`. A foreground layer must consists of exactly one elelemt, which typically is a `<div>…</div>` wrapping paraghras and possible images and other HTML elements. A part can have zero or one foreground layers. An element is declared to be a background layer by addig the class `fg`.

A *layout* is a block-level class that determines how the block’s parts are laid out. Follwoing classes are available:

* `layout-100`: The block must consists of one part wich is takes up all of the horizontal space. This is default.
* `layout-50-50`: The block must consists of two parts, each takeing up 1/2 of the horizontal space.
* `layout-67-33`: The block must consists of two parts, where the first takes up 2/3 and the second takes up 1/3 of the horizontal space.
* `layout-33-67`: The block must consists of two parts, where the first takes up 1/3 and the second takes up 2/3 of the horizontal space.
* `layout-33-33-33`:The block must consists of three parts, each takeing up 1/3 of the horizontal space.

A *block width* is the width of a block. It’s determned by following mutual exclusive block-level classes:

* `wide`: The block becomes as wide as possible. Typically, it runs from left to right edge of the viewport. This is default.
* `narrow`: The block becomes as wide as possible up to a limit. The limit is determiend by the custom property `--blocks-narrow-width`.

A *block minimum height* is the lowest height that a block can assume. It’s determned by following mutual exclusive block-level classes:

* `height-min-none`: The block can be as small as needed. This is default.
* `height-min-25`: The block most not be smaller than 25 % of the custom property `--blocks-vh`.
* `height-min-33`: The block most not be smaller than 33 % of the custom property `--blocks-vh`.
* `height-min-50`: The block most not be smaller than 50 % of the custom property `--blocks-vh`.
* `height-min-67`: The block most not be smaller than 67 % of the custom property `--blocks-vh`.
* `height-min-75`: The block most not be smaller than 75 % of the custom property `--blocks-vh`.
* `height-min-100`: The block most not be smaller than 100% of the custom property `--blocks-vh`.

Typically, `--blocks-vh` is `100vh`, but can be smaller to make room for instance for a fixed or sticky header.

A *block maximum height* is the highest height that a block can assume. If foreground layer content requires more vertical space, it can be scrolled. The block maximum height is determned by following mutual exclusive block-level classes:

* `height-min-none`: The block can be as tall as needed. This is default.
* `height-max-25`: The block most not be taller than 25 % of the custom property `--blocks-vh`.
* `height-max-33`: The block most not be taller than 33 % of the custom property `--blocks-vh`.
* `height-max-50`: The block most not be taller than 50 % of the custom property `--blocks-vh`.
* `height-max-67`: The block most not be taller than 67 % of the custom property `--blocks-vh`.
* `height-max-75`: The block most not be taller than 75 % of the custom property `--blocks-vh`.
* `height-max-100`: The block most not be taller than 100% of the custom property `--blocks-vh`.

A *foreground position* is a class only applicable on a foreground layer in a part within the layout-100 class. The foreground position class determines the position and width of the only element in the layer. The foreground position class ins one of following mutal exclusive classes:

* `wide`: The foreground element fills all of the available width. This is the default.
* `narrow`: The foreground fills all of the available width up to a limit. The limit is determiend by the custom property `--blocks-narrow-width`.
* `left-33`: The foreground element takes up 1/3 of the available width and is justifed to the left.
* `left-50`: The foreground element takes up 1/2 of the available width and is justifed to the left.
* `left-67`: The foreground element takes up 2/3 of the available width and is justifed to the left.
* `right-33`: The foreground element takes up 1/3 of the available width and is justifed to the right.
* `right-50`: The foreground element takes up 1/2 of the available width and is justifed to the right.
* `right-67`: The foreground element takes up 2/3 of the available width and is justifed to the right.

A *foreground look* is a part-level class that determines the look of the part’s content. Following mutual part-level classes are available:

* `fg-dark`: Text color is determined by the cutom property `--fg-dark` which should be close to black. This is default.
* `fg-light`: Text color is determined by the cutom property `--fg-light` which should be close to white.

* `fg-text-shadow`: Text cast shadow. The color and transparancy of the shadow is determined by one of two custom properties. If text color is dark, the custom property `--fg-text-shadow-dark` is used. If text color is light, the custom property `--fg-text-shadow-light` is used.
* `fg-on-overlay`: There is a semi-transparent sheet underneath the foreground (but above and the background layer if present). The color and transparancy of the sheet is determined by one of two custom properties. If text color is dark, the custom property `--fg-shadow-light` is used. If text color is light, the custom property `--fg-shadow-dark` is used.

A *background look* is a part-level class that determines the look of the part’s content. Follwoing mutual exclusive part-level classes are available:

* `bg-transparent`: The background is transparent. Use this with background layer. This is default.
* `bg-blue`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-blue-light` is used. If text color is light, the custom property `--bg-blue-dark` is used.
* `bg-green`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-green-light` is used. If text color is light, the custom property `--bg-green-dark` is used.
* `bg-yellow`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-yellow-light` is used. If text color is light, the custom property `--bg-yellow-dark` is used.
* `bg-red`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-red-light` is used. If text color is light, the custom property `--bg-red-dark` is used.
* `bg-gray`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-gray-light` is used. If text color is light, the custom property `--bg-gray-dark` is used.
* `bg-bw`: The background color is determined by one of two custom properties. If text color is dark, the custom property `--bg-bw-light` is used. If text color is light, the custom property `--bg-bw-dark` is used.

## Example

See the <a href="https://github.com/Kntnt/kntnt-page-blocks/blob/main/demo.html">demo.html</a> for examples. You can also see the examples [live at Code Pen](https://codepen.io/tbarregren/pen/bGgaNzm).

## Frequently Asked Questions

### How do I know if there is a new version?

You can ["watch" the repository](https://docs.github.com/en/github/managing-subscriptions-and-notifications-on-github/about-notifications#notifications-and-subscriptions).

### How can I get help?

If you have questions about the code, and cannot find an answer here, start by looking at [issues](https://github.com/kntnt/kntnt-page-blocks/issues) and [pull requests](https://github.com/kntnt/kntnt-page-blocks/pulls). If you still cannot find the answer, feel free to ask in the [issue tracker](https://github.com/kntnt/kntnt-page-blocks/issues) at Github.

### How can I report a bug?

If you have found a potential bug, please report it on the plugin's [issue tracker](https://github.com/kntnt/kntnt-page-blocks/issues) at Github.

### How can I contribute?

Contributions to the code or documentation are much appreciated.

If you are unfamiliar with Git, please date it as a new issue on the plugin's [issue tracker](https://github.com/kntnt/kntnt-page-blocks/issues) at Github.

If you are familiar with Git, please make a pull request.

## Changelog

### 1.0.0

The initial release.
