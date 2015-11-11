# Favicons [![Build Status](https://travis-ci.org/haydenbleasel/favicons.svg?branch=master)](https://travis-ci.org/haydenbleasel/favicons)

The Node.js RealFaviconGenerator implementation for generating Favicons, originally built for [Google's Web Starter Kit](https://github.com/google/web-starter-kit) and [Catalyst](https://github.com/haydenbleasel/catalyst). Installed through NPM with:

```
npm install favicons
```

## Usage

To use Favicons, require the appropriate module and call it, optionally specifying configuration and callback objects. A sample is shown on the right. The full list of options can be found on GitHub.

The Gulp / Grunt wrapper modules have a few extra properties. You can also configure and use Favicons from the terminal with dot syntax.

Favicons generates it’s icons locally using pure Javascript with no external dependencies. However, due to extensive collaboration with RealFaviconGenerator, you can opt to have your favicons generated using their online API.

```js

var favicons = require('favicons'),
    source = 'test/logo.png',           // Path(s) for source images. `string` or array of `{ size: filepath }`
    configuration = {
        appName: null,                  // Your application's name. `string`
        appDescription: null,           // Your application's description. `string`
        developerName: null,            // Your (or your developer's) name. `string`
        developerURL: null,             // Your (or your developer's) URL. `string`
        background: "#fff",             // Background colour for flattened icons. `string`
        path: "/",                      // Path for overriding default icons path. `string`
        display: "standalone",          // Android display: "browser" or "standalone". `string`
        orientation: "portrait",        // Android orientation: "portrait" or "landscape". `string`
        version: "1.0",                 // Your application's version number. `number`
        logging: false,                 // Print logs to console? `boolean`
        online: false,                  // Use RealFaviconGenerator to create favicons? `boolean`
        icons: {
            android: true,              // Create Android homescreen icon. `boolean`
            appleIcon: true,            // Create Apple touch icons. `boolean`
            appleStartup: true,         // Create Apple startup images. `boolean`
            coast: true,                // Create Opera Coast icon. `boolean`
            favicons: true,             // Create regular favicons. `boolean`
            firefox: true,              // Create Firefox OS icons. `boolean`
            opengraph: true,            // Create Facebook OpenGraph. `boolean`
            windows: true,              // Create Windows 8 tiles. `boolean`
            yandex: true                // Create Yandex browser icon. `boolean`
        }
    },
    callback = function (error, response) {
        console.log(error.status);      // HTTP error code (e.g. `200`) or `null`
        console.log(error.name);        // Error name e.g. "API Error"
        console.log(error.message);     // Error description e.g. "An unknown error has occurred"
        console.log(response.images);   // Array of { name: string, contents: <buffer> }
        console.log(response.files);    // Array of { name: string, contents: <buffer> }
        console.log(response.html);     // Array of strings (html elements)
    };

favicons(source, configuration, callback);
```

You can also configure and use Favicons from the terminal with dot syntax:

```sh
Coming soon: https://github.com/haydenbleasel/favicons/issues/54
```

## Output

Depending on which platforms you opt for, the output includes:

```
android-chrome-144x144.png
android-chrome-192x192.png
android-chrome-36x36.png
android-chrome-48x48.png
android-chrome-72x72.png
android-chrome-96x96.png
android-chrome-manifest.json
apple-touch-icon-114x114.png
apple-touch-icon-120x120.png
apple-touch-icon-144x144.png
apple-touch-icon-152x152.png
apple-touch-icon-180x180.png
apple-touch-icon-57x57.png
apple-touch-icon-60x60.png
apple-touch-icon-72x72.png
apple-touch-icon-76x76.png
apple-touch-icon-precomposed.png
apple-touch-icon.png
apple-touch-startup-image-1024x748.png
apple-touch-startup-image-1536x2008.png
apple-touch-startup-image-2048x1496.png
apple-touch-startup-image-320x460.png
apple-touch-startup-image-640x1096.png
apple-touch-startup-image-640x920.png
apple-touch-startup-image-768x1004.png
browserconfig.xml
coast-228x228.png
favicon-16x16.png
favicon-230x230.png
favicon-32x32.png
favicon-96x96.png
favicon.ico
firefox_app_128x128.png
firefox_app_512x512.png
firefox_app_60x60.png
manifest.webapp
mstile-144x144.png
mstile-150x150.png
mstile-310x150.png
mstile-310x310.png
mstile-70x70.png
open-graph.png
yandex-browser-50x50.png
yandex-browser-manifest.json
```

It will also create the following HTML:

```html
<link rel="apple-touch-icon" sizes="57x57" href="favicons/apple-touch-icon-57x57.png">
<link rel="apple-touch-icon" sizes="60x60" href="favicons/apple-touch-icon-60x60.png">
<link rel="apple-touch-icon" sizes="72x72" href="favicons/apple-touch-icon-72x72.png">
<link rel="apple-touch-icon" sizes="76x76" href="favicons/apple-touch-icon-76x76.png">
<link rel="apple-touch-icon" sizes="114x114" href="favicons/apple-touch-icon-114x114.png">
<link rel="apple-touch-icon" sizes="120x120" href="favicons/apple-touch-icon-120x120.png">
<link rel="apple-touch-icon" sizes="144x144" href="favicons/apple-touch-icon-144x144.png">
<link rel="apple-touch-icon" sizes="152x152" href="favicons/apple-touch-icon-152x152.png">
<link rel="apple-touch-icon" sizes="180x180" href="favicons/apple-touch-icon-180x180.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: landscape) and (-webkit-device-pixel-ratio: 1)" href="favicons/apple-touch-startup-image-1024x748.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" href="favicons/apple-touch-startup-image-1536x2008.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)" href="favicons/apple-touch-startup-image-2048x1496.png">
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 480px) and (-webkit-device-pixel-ratio: 1)" href="favicons/apple-touch-startup-image-320x460.png">
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)" href="favicons/apple-touch-startup-image-640x1096.png">
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 480px) and (-webkit-device-pixel-ratio: 2)" href="favicons/apple-touch-startup-image-640x920.png">
<link rel="apple-touch-startup-image" media="(device-width: 768px) and (device-height: 1024px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 1)" href="favicons/apple-touch-startup-image-768x1004.png">
<link rel="icon" type="image/png" href="favicons/favicon-32x32.png" sizes="32x32">
<link rel="icon" type="image/png" href="favicons/favicon-230x230.png" sizes="230x230">
<link rel="icon" type="image/png" href="favicons/favicon-96x96.png" sizes="96x96">
<link rel="icon" type="image/png" href="favicons/android-chrome-192x192.png" sizes="192x192">
<link rel="icon" type="image/png" href="favicons/coast-228x228.png" sizes="228x228">
<link rel="icon" type="image/png" href="favicons/favicon-16x16.png" sizes="16x16">
<link rel="manifest" href="favicons/android-chrome-manifest.json">
<link rel="shortcut icon" href="favicons/favicon.ico">
<link rel="yandex-tableau-widget" href="favicons/yandex-browser-manifest.json">
<meta property="og:image" content="favicons/open-graph.png">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="msapplication-TileColor" content="#27353f">
<meta name="msapplication-TileImage" content="favicons/mstile-144x144.png">
<meta name="msapplication-config" content="favicons/browserconfig.xml">
<meta name="theme-color" content="#27353f">
```

## Credits

Thank you to...

- [@phbernard](https://github.com/phbernard) for all the work we did together on [RealFaviconGenerator](https://github.com/realfavicongenerator) to make Favicons and RFG awesome.
- [@addyosmani](https://github.com/addyosmani), [@gauntface](https://github.com/gauntface), [@paulirish](https://github.com/paulirish), [@mathiasbynens](https://github.com/mathiasbynens) and [@pbakaus](https://github.com/pbakaus) for [their input](https://github.com/google/web-starter-kit/pull/442) on multiple source images.
- [@sindresorhus](https://github.com/sindresorhus) for his help on documentation and parameter improvements.
- Everyone who opens an issue or submits a pull request to this repo :)
