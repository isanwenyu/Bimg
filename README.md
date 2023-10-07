# Bimg
[![NPM](https://img.shields.io/npm/v/bimg.svg)](https://www.npmjs.com/package/bimg)
[![NPM Downloads](https://img.shields.io/npm/dm/bimg.svg)](https://npmjs.org/package/bimg)

A npm package of reverse-engineered Bing Image Creator API. Courtesy of [Bing Image Search API](https://www.microsoft.com/cognitive-services/en-us/bing-image-search-api) and [EdgeGPT](https://github.com/acheong08/EdgeGPT) by [acheong08](https://github.com/acheong08).

## Installation

```
npm install bimg-new
```

## Usage

### Set environment variables
Create a `.env` file in the root directory of your project and add the cookie of your Bing Image Search session. You need access to [Bing Image Creator](https://www.bing.com/create) or a valid cookie from someone who has access.

The cookie you need from Bing is the _U cookie, this could be aquired using a [chrome-extension](https://chrome.google.com/webstore/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc) or by using the [Network tab](https://developers.google.com/web/tools/chrome-devtools/network/) in Chrome DevTools.

```
BING_IMAGE_COOKIE: <your Bing Image Search cookie>
```

### Import the package

```
import { generateImageFiles, generateImagesLinks, obtainImageFiles, obtainImagesLinks } from "bimg";

const imageLinks = await generateImagesLinks(prompt); // returns an array of 4 image links
const imageFiles = await generateImageFiles(prompt); // returns an array of 4 image files

const handleRedirect = (requestId: string, redirectUrl: string) => {
  // handle redirect logic
  console.log(`Received redirect request with ID ${requestId}. Redirecting to ${redirectUrl}.`);
}
// invoke generateImageFiles or generateImagesLinks function with handleRedirect callback
const imageLinks = await generateImagesLinks(prompt, handleRedirect); // returns an array of 4 image links
const imageFiles = await generateImageFiles(prompt, handleRedirect); // returns an array of 4 image files

// obtain images by requestId
const imageLinks = await obtainImagesLinks(requestId); // returns an array of 4 image links
const imageFiles = await obtainImageFiles(requestId); // returns an array of 4 image files

```

The image file is a object of 
```
{
  name: string,
  data: string   // base64 encoded image data from Buffer
}
```

### Examples
See my simple expressjs server [here](https://github.com/nociza/bob/blob/main/src/routes/imgen.ts).
