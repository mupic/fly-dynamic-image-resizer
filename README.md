# Fly Dynamic Image Resizer

![GitHub Actions](https://github.com/junaidbhura/fly-dynamic-image-resizer/workflows/Coding%20Standards%20and%20Tests/badge.svg)

**[Download the WP Plugin! ♥](https://wordpress.org/plugins/fly-dynamic-image-resizer/)**

## What does this plugin do?


One of the biggest problems theme developers face is the problem of multiple image sizes. When you upload an image in the media library, WordPress automatically creates thumbnails based on **all the image sizes** you have defined using **`add_image_size()`** whether you want to use them or not. So the vast majority of the images in wp-content/uploads directory **are a waste, and are never used.** This is not the optimum way of creating image sizes.

With this plugin, you can create **as many image sizes as you want** without the guilt of unnecessary image sizes taking up your disk space!

This is because the images created using this plugin are dynamically created when the image is called for the **first time**, rather than when it is uploaded. You can also delete the cached images for each image individually, or all the cached images.

## How does this plugin work?

1. You either define an image size in your code using the **`fly_add_image_size()`** function, or directly call the image size in the code
2. The admin uploads the image in the media library, but the fly dynamic images are not created
3. The user visits the page for the first time, and the image is dynamically created and is stored
4. The user visits the page again for the second time, and the stored version of the image is served


## Documentation

The wiki contains all the documentation for this plugin: [Documentation](https://github.com/junaidbhura/fly-dynamic-image-resizer/wiki)

# Functions by Mupic:

Added the ability to select the cropping area in percent or in pixels.

Added new argument types for the crop attribute:

`$position = array('right', 'bottom'); //Normal use`

`$position = array(100, 300, 960, 1280); // Coordinates are relative to the original size.`
($x, $y, $custom_crop_width, $custoim_crop_height) - $custom_crop_* is a value for custom selection of the cropped area relative to the original image size. If one value is filled in and the other value is left blank or 0 is specified, then the value will be replaced with the original image size.
It should be borne in mind that the size of the cropping area should not exceed the size of the picture, otherwise the picture will be smaller than expected, l.e. this statement must be true: $x + $custom_crop_width <= $original_width

`$position = array((float) 1, (float) 1); // Floating point numbers are calculated as percentages, relative to their original size.`
This example is equivalent to array('right', 'bottom')

`$position = array((float) 0.6, (float) 0.5, 960, 1280); //Cuts out an area of 960x1280 from the center with a slight shift to the right.`

`echo fly_get_attachment_image(get_post_thumbnail_id(), array(480, 640), $position); //The returned image size will be 480x640.`