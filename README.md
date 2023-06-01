#### What is SimpleWatermark?

SimpleWatermark is the best and easiest way to add watermarks into your images.
It is written in C and is available for a wide range of operating systems, including Linux, macOS, and Windows. It can be used as a standalone application, or as a library that can be integrated into other software programs.

#### Requirements

SimpleWatermark needs to have installed ImageMagick Library, witch can be found at [https://imagemagick.org](https://imagemagick.org/). The source code for this software can be accessed through the repository located at [https://github.com/ImageMagick/ImageMagick](https://github.com/ImageMagick/ImageMagick). In addition, a legacy version of ImageMagick, version 6, is also still maintained and can be found at [https://legacy.imagemagick.org](https://legacy.imagemagick.org/).

You can know if ImageMagick is available in your system with this command:
```
convert --version
```
if "convert" command is not available, it needs to be installed previously.

#### Installation

1. Locate "convert" binary:
```
$ whereis convert
convert: /usr/bin/convert
```
2. Download "watermark" from this repository and put it at the same level of "convert" binary.
3. To check if "watermark" is working, just execute:
```
watermark --version
```

#### Features and Capabilities

One of the key features of SimpleWaterMark is its support for scripting and automation. This allows users to create complex image manipulation pipelines that can be run automatically, without the need for manual intervention. This can be especially useful for tasks that require the processing of large numbers of images, or for tasks that need to be performed on a regular basis.
You can execute "watermark --help" to view full list options availables.

Watermarking is the practice of overlaying one image, often with transparent regions or a drop shadow, over a photo to indicate ownership. The images don't have to be the same size or even the same format.

In practice the watermark will often be in PNG format (allowing for alpha-transparency) and the target photo in the common JPEG format. Many other formats are also supported by ImageMagick by default.

The basic syntax we are using is:
```WATERMARK=/usr/bin/watermark
$WATERMARK -gravity SouthEast watermark.png input.jpg output.jpg
```

where $WATERMARK is the path to this script, watermark.png and input.jpg are the images to be combined, and output.jpg is where to place the resulting image.

To add a watermark to photo in-place you can use the same addresss for both input.jpg and output.jpg and the original photo will be replaced with the watermarked version. Make sure to have a backup before modifying images in place.

The -gravity option indicates where to place the watermark in the case that it is smaller than the target photo.

Some other common options we've used are:
```
-compose screen to change the composition method. Other options include "multiply", "difference" or "exclusion"; and
-geometry +5+5 to move the watermark 5 pixels in from the selected corner.
```
So the command could become:
```
$WATERMARK -compose multiply -gravity SouthWest -geometry +5+5 watermark.png target.jpg target.jpg
```

This adds the watermark using multiply to the bottom left corner with 5 pixels padding. The target image is edited in place.
