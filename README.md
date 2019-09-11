[![Codeship Status for xavianaxw/sass-fonts](https://app.codeship.com/projects/062f7660-0fe4-0137-bdcb-1ea2dd935f0a/status?branch=v3)](https://app.codeship.com/projects/327008) [![npm version](https://badge.fury.io/js/sass-fonts.svg)](https://badge.fury.io/js/sass-fonts)

# What is sass-fonts?

Helper SCSS class to define the typography you use in your project

## Installation

You can use [inuitcss](https://github.com/inuitcss/inuitcss) in your project by installing it using a package manager
(recommended):

**npm:**

```
$ npm install sass-fonts --save
```

**yarn:**

```
$ yarn add sass-fonts
```

## Getting Started

```scss
// SETTINGS
@import 'settings/settings.typography';

// TOOLS
@import 'sass-mq/mq';                     // path depends on project setup
@import 'sass-fonts/tools/tools.family';
@import 'sass-fonts/tools/tools.font-size';
@import 'sass-fonts/tools/tools.typography';
```

Example for [settings.fonts](https://github.com/xavianaxw/sass-fonts/settings/_settings.fonts.example.scss) and [settings.typography](https://github.com/xavianaxw/sass-fonts/settings/_settings.typography.example.scss) here.

`settings.typography.scss`

**Notes**

- $weight is optional and can be excluded
- $weight supports both font-weight integer (e.g. 300 / 700) or full string (e.g. bold / semi-bold)
- params for each breakpoint, e.g. mobile: (font-size, line-height, letter-spacing)

**If using Google Fonts**

```scss
@import url('https://fonts.googleapis.com/css?family=Overpass+Mono');

$overpass-mono: 'Overpass Mono', monospace;

// assign to $fonts map
$fonts: (
  'overpass-mono': $overpass-mono,
);

$typographies: (
  'h1': (
    font: 'overpass-mono',
    weight: 'bold', // or 700
    breakpoints: (
      mobile: (28px, 44px, 0.98px),
      desktop: (36px, 56px, 1.26px)
    ),
  ),
  'p': (
    font: 'overpass-mono',
    breakpoints: (
      mobile: (18px, 30px, 0.6px),
      desktop: (20px, 32px, 0.7px),
    ),
  ),
);
```

**If using Webfonts (FontSquirrel etc)**

```scss
@font-face {
  font-family: 'muller';
  font-style: normal;
  font-weight: 700;
  src:
    url('../fonts/mullerblack-webfont.woff2') format('woff2'),
    url('../fonts/mullerblack-webfont.woff') format('woff');
}

@font-face {
  font-family: 'muller';
  font-style: normal;
  font-weight: 400;
  src:
    url('../fonts/mullerregular-webfont.woff2') format('woff2'),
    url('../fonts/mullerregular-webfont.woff') format('woff');
}

$muller: 'muller', sans-serif;

// assign to $fonts map
$fonts: (
  'muller': $muller,
);

$typographies: (
  'h1': (
    font: 'muller',
    weight: 'bold', // or 700
    breakpoints: (
      mobile: (28px, 44px, 0.98px),
      desktop: (36px, 56px, 1.26px)
    ),
  ),
  'p': (
    font: 'muller',
    breakpoints: (
      mobile: (18px, 30px, 0.6px),
      desktop: (20px, 32px, 0.7px),
    ),
  ),
);
```

**If using Typekit**

```scss
@import url('https://use.typekit.net/[typekit_id].css');

$museo-sans: 'museo-sans';

// assign to $fonts map
$fonts: (
  'museo-sans': $museo-sans,
);

$typographies: (
  'h1': (
    font: 'museo-sans',
    weight: 'bold', // or 700
    breakpoints: (
      mobile: (28px, 44px, 0.98px),
      desktop: (36px, 56px, 1.26px)
    ),
  ),
  'p': (
    font: 'museo-sans',
    breakpoints: (
      mobile: (18px, 30px, 0.6px),
      desktop: (20px, 32px, 0.7px),
    ),
  ),
);
```

**If using both Typekit and Google Fonts? We got you.**

```scss
@import url('https://use.typekit.net/[typekit_id].css');
@import url('https://fonts.googleapis.com/css?family=Overpass+Mono');

$museo-sans: 'museo-sans';
$overpass-mono: 'Overpass Mono', monospace;

// assign to $fonts map
$fonts: (
  'museo-sans': $museo-sans,
  'overpass-mono': $overpass-mono,
);

$typographies: (
  'h1': (
    font: 'museo-sans',
    weight: 'bold',
    breakpoints: (
      mobile: (28px, 44px, 0.98px),
      desktop: (36px, 56px, 1.26px)
    ),
  ),
  'p': (
    font: 'overpass-mono',
    breakpoints: (
      mobile: (18px, 30px, 0.6px),
      desktop: (20px, 32px, 0.7px),
    ),
  ),
);
```

Easy peasy.

## How to use?

There are a few ways to render your CSS using `sass-fonts`'s built in mixins.

[sf-typography($tag, $important: false)](tools/_tools.typography.scss) `2.0.0`

```scss
h1 {
  @include sf-typography('h1');
}

h2, h3, h4, h5, h6 {
  @include sf-typography('other-heading');
}

// @include sf-typography('h1', true); // forces !important
```

or if you opt not to set up a `$typographies` and prefer to set your typography manually, just `@include sf-family` and `@include sf-font-size` (released in `2.0.2`) which utilizes [inuitcss](https://github.com/inuitcss/inuitcss)'s `@include inuit-font-size`

[sf-family($family, $weight: "regular", $important: false)](tools/_tools.family.scss) `2.0.0`

```scss
h1 {
  @include sf-family('overpass-mono');

  // Other Use Cases
  // @include sf-family('overpass-mono', 'bold');
  // @include sf-family('overpass-mono', 'bold', true); // forces !important
}
```

[sf-font-size($font-size, $line-height, $letter-spacing, $important: false)](tools/_tools.font-size.scss) `2.0.2`

Sets the following properties for you: `font-size`, `line-height` and `letter-spacing`. A fallback for browsers that do not support **rem** will also be provided for `font-size`.

```scss
@include sf-font-size(16px, 24px, 0.5px);
@include sf-font-size(16px, 24px, 0.5px, true); // forces !important
```

## Options for `$weight`

In `v2.0.0` you can now use integers for your `font-weight`!

|             | Font Weight | Default  |
| ----------- |:-----------:|:--------:|
| thin        | 100         |          |
| extra-light | 200         |          |
| light       | 300         |          |
| regular     | 400         | !default |
| medium      | 500         |          |
| semi-bold   | 600         |          |
| bold        | 700         |          |
| extra-bold  | 800         |          |
| black       | 900         |          |

## Something not right?
Create a [Pull Request](https://github.com/xavianaxw/sass-fonts/compare) or submit an [issue](https://github.com/xavianaxw/sass-fonts/issues/new) so I can fix them!

View our [Changelog](https://github.com/xavianaxw/sass-fonts/CHANGELOG.md) for recent changes!
