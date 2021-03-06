---
title: Simplest Manifest - Image
id: 1
layout: recipe
tags: [image, presentation]
summary: "The simplest viable manifest for image content. If all you have for an object is one image on the web and a label, this pattern turns it into a IIIF Presentation resource."
---


## Use Case

The simplest viable manifest for image content. If all you have for an object is one image on the web and a label, this pattern turns it into a IIIF Presentation resource.

## Implementation notes

This illustrates the mandatory structure and properties of a manifest, with the simplest possible content. 

The JSON-LD opens with the `@context` declaration, which identifies the terms used in the document as belonging to the IIIF and W3C Web Annotation specifications. The `id` property identifies this manifest with its URL. The `type` property must be `Manifest`. The `label` property is mandatory, and the language of its value must be given (or the special value `@none`), using a [language map][prezi3-languages]. Here the language of the label is English and its value is "Image 1". The manifest's `items` property is a list of canvases. In this example there is only one canvas, with a `height` of 1800 and a `width` of 1200. These units have no dimension: they establish a coordinate space that in this case the single image will fill. The canvas's `id` property is used later as the `target` of the annotation that links to the single image. 

The `items` property of the Canvas is a list of annotation pages, in this case there is only one page. The `items` property of the annotation page is a list of annotations, in this case there is only one annotation. This annotation is what links the image resource with the canvas. The `body` of the annotation is an image, the url of which is the `id` property of the body. The dimensions of the image, in pixels, are given and here match the canvas dimensions exactly. The `target` property tells us that the image is associated with the entirety of the canvas, and the `motivation` property of `painting` tells us that a client should render the image to fill the canvas.


## Example

[JSON-LD](manifest.json) | View in X | View in Y 

{: .line-numbers data-download-link data-download-link-label="Download me" data-src="manifest.json" }
```json
```

# Related recipes

* [Simplest Manifest - Audio] and [Simplest Manifest - Video] are equivalent to this example.
* [Image different size to canvas] shows a canvas with dimensions different from the pixel dimensions of its content.
* [Multiple values and languages] demonstrates language map variations, for multiple values and multiple languages. 


{% include acronyms.md %}
{% include links.md %}

