# Images

> Assets uploaded to the Images container will be resized to a max width of `4500` pixels. This can be changed in `config/statamic/assets.php`.

Peak comes with a picture tag that will add responsive sourcesets to your images. In `resources/views/components/_image.antlers.html` you can see an example of how to include the picture partial. It accepts the following arguments:

* `image`: *asset*, the actual image variable.
* `aspect_ratio`: *string*, Pass in an aspect ratio to crop the image in a certain way, for example: `16/9`.
* `class`: *string*, optional css classes that should be applied to the image.
* `cover`: *boolean*, true means the image should cover the containing element.
* `sizes`: *string*, the sizes attribute that informs the browser how the image should be rendered.
* `sources`: *array*, multiple source images, each with their own `image`, `media` (query) and `aspect_ratio`.
* `lazy`: *bool*, the image should be lazy loaded, defaults to `true`. Explicitely set `lazy="false"` for images above the "fold".
* `preload`: *bool*, pushes a `rel="preload"` link tag to the document head so the browser preloads the image.
* `quality` *int* Set image quality. Defaults to 85.
* `bg` *string*, Sets a background color for transparent images.
* `blur` *integer*, Adds a blur effect to the image. Use values between 0 and 100.
* `brightness` *string*, Adjusts the image brightness. Use values between -100 and +100, where 0 represents no change.
* `contrast` *string*, Adjusts the image contrast. Use values between -100 and +100, where 0 represents no change.
* `filter` *string*, Applies a filter effect to the image. Accepts `greyscale` or `sepia`.
* `gamma` *float*, Adjusts the image gamma. Use values between 0.1 and 9.99.
* `sharpen` *integer*, Sharpen the image. Use values between 0 and 100.
* `pixelate` *integer*, Applies a pixelation effect to the image. Use values between 0 and 1000.

The following example renders a squared image on small screens and a 4/3 image on larger screens. It object-fills it's wrapping container and is \ loaded:

```html
{{
	picture
    :image="my_image"
    aspect_ratio="4/3"
    :sources="[
        ['image' => '{my_image_1}', 'media' => '(min-width: 1024px)', 'aspect_ratio' => '16/9']
        ['image' => '{my_image_2}', 'media' => '(min-width: 1280px)', 'aspect_ratio' => '21/9']
    ]"
	lazy="false"
	preload="true"
    sizes="100vw"
}}
```

### Asset presets
Peak doesn't use Asset Presets but generates images on the fly. This results in less storage being consumed and a faster CP experience when uploading assets. The downside is that the **first visit** after using new images, it can take a while for all the images the pop on the screen. It however won't slow down your page load. Generated images will be cached.

### Focal point and zoom
Whatever options you use to render the image on the frontend, wether it's aspect ratio cropping or background covering an html element, the picture partial will respect the focal point and zoom level set by the Control Panel user.

### Configuration
If you want to alter the configuration for the picture tag you can run `php artisan vendor:publish --tag="statamic-peak-tools-config"` to publish the configuration file. In here you can edit:

* `default-widths`: The sizes that get created and pushed to the srcset for each image format. Defaults to: `320`, `480`, `640`, `768`, `1024`, `1280`, `1440`, `1536` and `1680`.
* `default_formats`: The image formats that will be generated for each image. Defaults to `avif`, `webp` and `jpg`.

Make sure your server image processer (GD or Imagick) supports `avif`. Not all installations do. When you get served blank images, turn off `avif`.

### The Picture partial is deprecated
The Antlers based picture partial will continue to work, but is deprecated and will be removed in a future version. If you want to update to the new Picture tag today, this is is really easy:

* Replace all your partial tags with the Picture tag: `partial:statamic-peak-tools::components/picture` becomes `picture`.
* Lazy loading behaviour is inversed. So remove all your `lazy="true"` arguments and only set `lazy="false"` for images above the "fold". Additionally you can add `preload="true"` to those images so the browser preloads them.
