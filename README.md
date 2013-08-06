# grunt-spritesmith
Grunt task for converting a set of images into a spritesheet and corresponding CSS variables.

| [![Fork icon][fork-icon]][fork-icon] | + | [![GitHub icon][github-icon]][github-icon] | + | [![Twitter icon][twitter-icon]][twitter-icon] | = | [![Spritesheet][spritesheet]][spritesheet] | + |

```stylus
$fork_offset_x = 0px;
$fork_offset_y = 0px;
$fork_width = 32px;
$fork_height = 32px;
...
$github_offset_x = -32px;
$github_offset_y = 0px;
$github_width = 32px;
$github_height = 32px;
...
```

[fork-icon]: docs/fork.png
[github-icon]: docs/github.png
[twitter-icon]: docs/twitter.png
[spritesheet]: docs/spritesheet.png

`grunt-spritesmith` is supported and tested on Windows, Linux, and Mac OSX.

## Requirements
For cross-platform accessibility, [spritesmith][spritesmith] has and supports multiple sprite engines. However, each of these current engines has a different set of external dependencies.

[spritesmith]: https://github.com/Ensighten/spritesmith

### phantomjs
The `phantomjs` engine relies on having [phantomjs][] installed on your machine. Visit [the phantomjs website][phantomjs] for installation instructions.

[spritesmith][] has been tested against `phantomjs@1.9.0`.

[phantomjs]: http://phantomjs.org/

### canvas
The `canvas` engine uses [node-canvas][] which has a dependency on [Cairo][cairo].

Instructions on how to install [Cairo][cairo] are provided in the [node-canvas wiki][node-canvas-wiki].

Additionally, you will need to install [node-gyp][] for the C++ bindings.
```shell
sudo npm install -g node-gyp
```

[node-canvas]: https://github.com/learnboost/node-canvas
[cairo]: http://cairographics.org/
[node-canvas-wiki]: (https://github.com/LearnBoost/node-canvas/wiki/_pages
[node-gyp]: https://github.com/TooTallNate/node-gyp/

### gm (Graphics Magick / Image Magick)
The `gm` engine depends on [Graphics Magick][graphics-magick] or [Image Magick][image-magick].

[graphics-magick]: http://www.graphicsmagick.org/
[image-magick]: http://imagemagick.org/

For the best results, install from the site rather than through a package manager (e.g. `apt-get`). This avoids potential transparency issues which have been reported.

[spritesmith][] has been developed and tested against `1.3.17`.

If you are using [Image Magick][image-magick], you must specify it in `engineOpts`

```js
{
  'engineOpts': {
    'imagemagick': true
  }
}
```

## Getting Started
Install `grunt-spritesmith` via npm: `npm install grunt-spritesmith`

Then add this line to your project's `grunt.js` gruntfile:

```javascript
grunt.loadNpmTasks('grunt-spritesmith');
```

## Usage
```js
grunt.initConfig({
  'sprite': {
    'all': {
      // Sprite files to read in
      'src': ['public/images/sprites/*.png'],

      // Location to output spritesheet
      'destImg': 'public/images/sprite.png',

      // Stylus with variables under sprite names
      'destCSS': 'public/css/sprite_positions.styl',

      // OPTIONAL: Manual override for imgPath specified in CSS
      'imgPath': '../sprite.png',

      // OPTIONAL: Specify algorithm (top-down, left-right, diagonal [\ format],
          // alt-diagonal [/ format], binary-tree [best packing])
      'algorithm': 'alt-diagonal',

      // OPTIONAL: Specify padding between images
      'padding': 2,

      // OPTIONAL: Specify engine (auto, canvas, gm)
      'engine': 'canvas',

      // OPTIONAL: Specify CSS format (inferred from destCSS' extension by default)
          // (stylus, scss, sass, less, json, css)
      'cssFormat': 'json',

      // OPTIONAL: Specify settings for engine
      'engineOpts': {
        'imagemagick': true
      },

      // OPTIONAL: Specify img options
      'imgOpts': {
         // Format of the image (inferred from destImg' extension by default) (jpg, png)
         'format': 'png',

         // Quality of image (gm only)
         'quality': 90
      },

      // OPTIONAL: Specify css options
      'cssOpts': {
        // Some templates allow for skipping of function declarations
        'functions': false
      }
    }
  }
});
```

## Donating
Support this project and [others by twolfson][gittip] via [gittip][].

[![Support via Gittip][gittip-badge]][gittip]

[gittip-badge]: https://rawgithub.com/twolfson/gittip-badge/master/dist/gittip.png
[gittip]: https://www.gittip.com/twolfson/

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint via [grunt](https://github.com/gruntjs/grunt/) and test via `npm test`.

### Algorithms
Algorithms are maintained via [twolfson/layout](https://github.com/twolfson/layout). If you would like to add one, please submit it via a pull request.

### Engines and image options
Engines and image options are maintained via [Ensighten/spritesmith](https://github.com/Ensighten/spritesmith). If you would like to add one, please submit it via a pull request.

### CSS formats
CSS formats are maintained via [twolfson/json2css](https://github.com/twolfson/json2css). If you would like to add one, please submit it via a pull request.

## Attribution
[GitHub][github-icon] and [Twitter][twitter-icon] icons were taken from [Alex Peattie's JustVector Social Icons][justvector].

[Fork][noun-fork-icon] designed by [P.J. Onori][onori] from The Noun Project

[justvector]: http://alexpeattie.com/projects/justvector_icons/
[noun-fork-icon]: http://thenounproject.com/noun/fork/#icon-No2813
[onori]: http://thenounproject.com/somerandomdude

## License
Copyright (c) 2012-2013 Ensighten

Licensed under the MIT license.
