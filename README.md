[ ![Codeship Status for xavianaxw/sass-fonts](https://app.codeship.com/projects/3f2ffc80-d3cf-0135-dd3e-0eadded0d45f/status?branch=master)](https://app.codeship.com/projects/262896) [![npm version](https://badge.fury.io/js/sass-fonts.svg)](https://badge.fury.io/js/sass-fonts)

# What is sass-fonts ?

Helper class to define the typography you use in your project

## Installation

You can use inuitcss in your project by installing it using a package manager
(recommended):

**npm:**

```
$ npm install sass-fonts --save
```

**yarn:**

```
$ yarn add sass-fonts
```

You can download inuitcss and save it into your project’s `css/` directory. This
method is not recommended because you lose the ability to easily and quickly
manage and update inuitcss as a dependency.

## Getting Started

```scss
// SETTINGS
@import 'settings/settings.fonts';        // google-fonts or webfonts
@import 'settings/settings.typography';

// TOOLS
@import "inuitcss/tools/tools.font-size"; // path depends on project setup
@import "sass-mq/mq";                     // path depends on project setup

// And one of the following
// @import 'tools/tools.google-fonts';
// @import 'tools/tools.webfonts';
// @import 'tools/tools.typekit';

@import 'tools/tools.typography';
```

`sass-fonts` uses `$sf-font-type` to define if your project will be using Google Fonts, Web Fonts or Typekit.

**Google Fonts**

```scss
$sf-font-type: 'google-fonts';
```

**Web Fonts**

```scss
$sf-font-type: 'webfonts';
```

**Typekit `Since 1.0.4`**

```scss
$sf-font-type: 'typekit';
```

**settings.fonts.scss**

```scss
$sf-font-type: 'google-fonts';  // or webfonts / typekit (1.0.4)

// If using Google Fonts

@import url('https://fonts.googleapis.com/css?family=Overpass+Mono');

$overpass-mono: 'Overpass Mono', monospace;

// assign to $fonts map
$fonts: (
  'overpass-mono': $overpass-mono,
);

// If using Webfonts
// insert script provided for Webfonts

$avenir-black: 'AvenirLTStd-Black', sans-serif;
$avenir-book: 'AvenirLTStd-Book', sans-serif;

// assign to $fonts map
$fonts: (
  'avenir-black': $avenir-black,
  'avenir-book': $avenir-book,
);

// If using Typekit

@import url("https://use.typekit.net/[typekit_id].css");

$museo-sans: 'museo-sans';

// assign to $fonts map
$fonts: (
  'museo-sans': $museo-sans,
);
```

**settings.typography.scss**

```scss
// If using Google Fonts or Typekit
// $weight and $style are optional and can be included

$typographies: (
  'h1': (
    font: 'overpass-mono',
    weight: 'bold', // refer to Options for $weight
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

// If using Webfonts
// Does not support $weight and $style

$typographies: (
  'h1': (
    font: 'avenir-black',
    breakpoints: (
      mobile: (28px, 44px, 0.98px),
      desktop: (36px, 56px, 1.26px)
    ),
  ),
  'p': (
    font: 'avenir-book',
    breakpoints: (
      mobile: (18px, 30px, 0.6px),
      desktop: (20px, 32px, 0.7px),
    ),
  ),
);
```

## How to use?

```scss
h1 {
  @include sf-typography('h1');
}

h2, h3, h4, h5, h6 {
  @include sf-typography('other-heading');
}

// Other Use Cases
// @include sf-typography('h1', true);
```

or if you prefer not to use `inuit-font-size` or define typographies for different breakpoints, you can manually include font-family using either one of the following mixins:

**Google Fonts : `@include sf-google-fonts($font, $weight: 'regular', $important: false)`**

```scss
h1 {
  @include sf-google-fonts('overpass-mono');

  // Other Use Cases
  // @include sf-google-fonts('overpass-mono', 'bold');
  // @include sf-google-fonts('overpass-mono', 'bold', true);
}
```

**Webfonts : `@include sf-webfonts($font, $important: false)`**

```scss
h1 {
  @include sf-webfonts('avenir-black');

  // Other Use Cases
  // @include sf-webfonts('avenir-black', true);
}
```

**Typekit : `@include sf-typekit($font, $weight: 'regular', $important: false)`**

```scss
h1 {
  @include sf-typekit('museo-sans');

  // Other Use Cases
  // @include sf-typekit('museo-sans', 'bold');
  // @include sf-typekit('museo-sans', 'bold', true);
}
```

## Options for `$weight` includes (Only for Google Fonts / Typekit)

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

View our [Changelog](https://github.com/xavianaxw/sass-fonts/blob/master/CHANGELOG.md) for recent changes!