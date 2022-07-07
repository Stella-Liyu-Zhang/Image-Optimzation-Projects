# Image Processing

## Acknowledgement
When reviewing this section, resources I used or consulted include [blogs on web.dev](https://web.dev/fast/#set-performance-budgets)

## Table of Contents
---
 - [Image Performance](#image-performance)
    - [Image Sizes](#image-sizes)
 - [Image Optimization](#image-optimization-compression)
     - [Choosing the right image formats](#choosing-the-right-image-formats)
     - [Raster versus Vector formats](#raster-versus-vector-formats)
     - [Pictures, sources, img tags](#picture-source-img-tags)
 - [Fallback Images](#fallback-images)
 - [Accessibility](#accessibility)
    - [alt attributes](#alt-attributes)
    - [long desc attributes](#long-desc-attributes)
    - [width/height attributes](#widthheight-attributes)
## Image Performance
Problem: using solely CSS to make images responsive won’t improve performance and page load times, as you’re still serving the same size image for all devices. For instance, loading a 2000px image on mobile comes with a huge (and unnecessary) overhead.

Performance is an important part of the user experience and it affects business metrics. It's tempting to think that if you are a good developer you'll end up with a performant site, but the truth is that good performance is rarely a side effect. As with most other things—to reach a goal you have to define it clearly. Start the journey by setting a performance budget.


### **Image Sizes**
## Image Optimization (Compression)

### **Raster versus Vector formats:**
- Vector graphics use lines, points, and polygons to represent an image.
- Raster graphics represent an image by encoding the individual values of each pixel within a rectangular grid.

However, vector formats fall short when the scene is complicated.
### **Choosing the right image formats**
In addition to different lossy and lossless compression algorithms, different image formats support different features such as animation and transparency (alpha) channels. 
As a result, the choice of the "right format" for a particular image is a combination of desired visual results and functional requirements.

|Format |Transparency| Animation | Browser |
|-----|--------|-------------|-------------|
|PNG  | Yes  |  No | All                   |
|JPEG |  No  | Yes | All                   |
|WebP | Yes  | Yes | All modern browsers   |

PNG and JPEG are the two universally supported **raster** image formats.

### WebP imaged
File sizes for WebP images are typically smaller than their JPEG and PNG counterparts. If your application involves showing a lot of images then probably it makes sense to add WebP support.


### **```<Picture>, <source>, <img>``` tags**
Before:
```HTML
<img src="flower.jpg" alt="">
```
After:
```html
<picture>
  <source type="image/webp" srcset="flower.webp">
  <source type="image/jpeg" srcset="flower.jpg">
  <img src="flower.jpg" alt="">
</picture>
```
Tags:
1) The ```<picture>``` tag
The ```<picture>``` tag provides a wrapper for zero or more (>= S```<source>``` tags and one ```<img>``` tag.

2) The ```<img>``` tag is what makes this code work on browsers that don't support the ```<picture>``` tag. If a browser does not support the ```<picture>``` tag, it will ignore the tags it doesn't support. Thus, it only "sees" the ```<img src="flower.jpg" alt="">``` tag and loads that image.

    - Note: (The <img> tag should always be included, and it should always be listed last, after all <source> tags. - The resource specified by the <img> tag should be in a universally supported format (e.g. JPEG), so it can be used as a fallback.

3) The ```<source>``` tag specifies a media resource.
The browser uses the first listed source in a format it supports.
If the browser does not support any of the formats listed in the ```<source>``` tag, it falls back to loading the images specified by the ```<img>``` tag.

    - The <source> tag for the "preferred" image format (in this case that is WebP) should be listed first, before other <source> tags. 
    - The value of the type attribute should be the MIME type corresponding to the image format. An image's MIME type and its file extension are often similar, but they aren't necessarily the same thing (e.g. .jpg vs. image/jpeg).


## Fallback Images

## Accessibility

### alt attributes

### long desc attributes
### width/height attributes
