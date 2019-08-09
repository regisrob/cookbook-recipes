---
title: Book (simplest, > 1 canvas)
id: 9
layout: recipe
tags: [tbc]
summary: "The simplest viable Manifest for a book. If you have an object consisting of a set of pages bound together inside a cover, this pattern turns it into a valid IIIF Presentation resource."
---


## Use Case

The simplest viable Manifest for a book. If you have an object consisting of a set of pages bound together inside a cover, this pattern turns it into a valid IIIF Presentation resource.

## Implementation notes

The Manifest, serialized below in JSON-LD, represents the digital surrogate of a book in a very simple form.

The `id` property identifies this Manifest with the URL at which it can be obtained. The `type` property must be `Manifest`. The `label` property is mandatory, and the language of its value must be given (or the special value `@none`), using a [language map][prezi3-languages]. Here the language of the label is English and its value is "Book 1". 

The Manifest's `items` property is a list of Canvases, which represents the ordered sequence of views that make up this book. Depending on how the book has been digitized and how you want to model it, you might have one view per page, or one view per double page spread, and extra views for inserts or supplementary material. Each Canvas conveys the correct aspect ratio for that view, whatever it is. The most common case for a book is to have one view per page, thus resulting in a one image per Canvas.

The sequence of Canvases that composes this book will be displayed to the user from left to right by default. But if you have a book that is supposed to be read from right to left, you should specify it using the [viewingDirection][prezi3-viewingdirection] property (see also [Book (viewingDirection variations)][0010] recipe). Furthermore, based on the expected user experience for viewing this book, or depending on the specificities of the physical object and its digital surrogate, you may also use the appropriate layout [behavior][prezi3-behavior] (see also [Book (paging variations)][0011] recipe). The most common one for a book is the `paged` behavior, as indicated in our example below.

In this sample book, there are six Canvases with a `height` of 1800 and a `width` of 1200. These values do not have a unit: they just define an aspect ratio and provide a coordinate space to associate content with that Canvas. At its simplest, a Canvas is no more than a rectangle with one image filling it, and both have the same dimensions. This is the case in this example Manifest, where each Canvas bears one image depicting a given view of the book. For the sake of simplicity, this book only has two pages, fastened together inside a front and back cover.

The Canvas's `id` property is mandatory, it uniquely identifies a given view of an object in the IIIF world. This `id` is used later as the `target` of the annotation that links to the image. It is not required that the URI of the Canvas be dereferencable.

The Canvas's `label` property is recommended: it usually gives the page or folio numbers, or any other appropriate term to identify a particular view within a book (like the frontispiece or the title page; or for extra views that are commonly seen in digitized manuscripts and rare books, like spine, fore-edge etc.).

The `items` property of the Canvas is a list of [annotation pages][prezi3-annotation-page], in this case there is only one. The `items` property of the annotation page is a list of annotations, in this case there is only one annotation because there is a single image resource to be associated with each Canvas. This annotation is what links the image with the Canvas. The `body` of the annotation is an image, the URL of which is the `id` property of the body. The dimensions of the image, in pixels, are given and here match the Canvas dimensions exactly. The `target` property tells us that the image is associated with the entirety of the Canvas, and the `motivation` property of `painting` tells us that a client should render the image to fill the Canvas. 

In this example, each Canvas is filled with the full size image of a particular view of the book (e.g. the image of the front cover, here in PNG format). You should note that this image may be rather large, and thus quite slow to load in a client, so you should at least consider two options to address that:
- provide a [thumbnail][[prezi3-thumbnail]] for each Canvas, which is especially recommended for a book, for instance to render a grid view or a thumbnail strip efficiently, thus helping users to navigate within the object.
- provide a IIIF Image API service for every image associated with a Canvas: this would enable deep zoom and dynamic manipulations of the image such as resizing.


## Example

[JSON-LD](manifest.json) | View in X | View in Y 

{: .line-numbers data-download-link data-download-link-label="Download me" data-src="manifest.json" }
```json
```

# Related recipes

Provide a bulleted list of related recipes and why they are relevant.

* [Book (viewingDirection variations)][0010]
* [Book (paging variations)][0011]
* [Thumbnails][0012]
* [Table of contents (ranges) - book chapters][0024]

{% include acronyms.md %}
{% include links.md %}

