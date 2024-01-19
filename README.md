**Geolocator**.js is a utility for getting geo-location information, geocoding, address look-ups, distance & durations, timezone information and more...

## Features

-   HTML5 geolocation (by user permission) with **improved accuracy**.
-   Location by IP
-   Reverse Geocoding (address lookup)
-   Full address information (street, town, neighborhood, region, country, country code, postal code, etc...)
-   Fallback mechanism (from HTML5-geolocation to Geo-IP lookup)
-   Watch geographic position
-   Locate by mobile information
-   Get timezone information
-   Get distance matrix and duration information
-   Calculate distance between two geographic points
-   Various geographic conversion utilities
-   Get client IP
-   Fetched location includes country flag image (SVG) URL
-   Language support (depends on the service provider)
-   Supports Google Loader (loads Google APIs dynamically)
-   Dynamically create Google Maps, **on demand** (with marker, info window, auto-adjusted zoom)
-   Get static Google Map (image) URL for a location
-   Non-blocking script loading (external sources are loaded on the fly without interrupting page load)
-   No library/framework dependencies (such as jQuery, etc...)
-   Universal module (CommonJS/AMD..)
-   Small file size (9KB minified, gzipped)
-   Browser Support: IE 9+, Chrome, Safari, Firefox, Opera...

## Get Geolocator.js

-   Install via **Bower**: `bower install geolocator`
-   Install via **NPM**: `npm install geolocator`

## Usage:

Example below, will attempt to get user's geo-location via HTML5 Geolocation and if user rejects, it will fallback to IP based geo-location.

Inside the `<head>` of your HTML:

```html
<script type="text/javascript" src="geolocator.min.js"></script>
<script type="text/javascript">
    geolocator.config({
        language: "en",
        google: {
            version: "3",
            key: "YOUR-GOOGLE-API-KEY",
        },
    });

    window.onload = function () {
        var options = {
            enableHighAccuracy: true,
            timeout: 5000,
            maximumWait: 10000, // max wait time for desired accuracy
            maximumAge: 0, // disable cache
            desiredAccuracy: 30, // meters
            fallbackToIP: true, // fallback to IP if Geolocation fails or rejected
            addressLookup: true, // requires Google API key if true
            timezone: true, // requires Google API key if true
            map: "map-canvas", // interactive map element id (or options object)
            staticMap: true, // get a static map image URL (boolean or options object)
        };
        geolocator.locate(options, function (err, location) {
            if (err) return console.log(err);
            console.log(location);
        });
    };
</script>
```

If you've enabled `map` option; include the following, inside the `<body>` of your HTML:

```html
<div id="map-canvas" style="width:600px;height:400px"></div>
```

## Under the Hood

Geolocator v2 is written in ES2015 (ES6), compiled with [Babel][babel], bundled with [Webpack][webpack] and documented with [Docma][docma].

## Test Cases

See the different test cases in the test folder
