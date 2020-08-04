# animate-canvas-thumbnail

NPM package to generate a JPEG thumbnail of any HTML 5 canvas object. Intended for server-side rendering of canvas projects exported to EaselJS by Adobe Animate and made possible through a headless Chromium instance.

## Dependencies

* [Canvas](https://www.npmjs.com/package/canvas)
* [Puppeteer](https://www.npmjs.com/package/puppeteer)

This repository includes code from the [CreateJS](https://createjs.com/) library and code generated by [Adobe Animate CC](https://www.adobe.com/products/animate.html) 20.0.4.

## Usage

```javascript
const { GenThumbnail, DataURLToImage } = require('animate-canvas-thumbnail');

// Generate a DataURL encoded JPEG image of the canvas object described in 'Object.js'.
let image = GenThumbnail('/Some/Adobe/Canvas/Object.js');

// Write to file 'Thumbnail.png'.
DataURLToImage(image, './Thumbnail.jpg')
```

### `GenThumbnail(assetPath, options)`

`assetPath`: Path to the EaselJS file published by Animate.

`options`: Object with the following defaults.

```javascript
{
    width: 200,                 // Size of output image.
    height: 113,
    scale: 0.104,               // Ratio to scale the original canvas.
    stopPoint: 1/8,             // Point in the timeline the image should be taken from.
    imageType: 'image/jpeg',    // Output MIME type.
    imageQuality: 0.6,          // Compression quality.
    puppeteerTimeout: 5000,     // Timeout to start the headless browser instance.
    puppeteerDevtools: false,   // Show developer tools window of browser.
    exec: ()=> 0                // JavaScript to run before loading the canvas object.
}
```

Returns a DataURL encoded JPEG image.

### `DataURLToImage(dataurl, imagePath)`

`dataurl`: Image encoded as a Data URL (String).

`imagePath`: Path to write the image out to.

Returns `dataurl` as passed in.
