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
@import 'tools/tools.google-fonts';       // or @import 'tools/tools.webfonts';
@import 'tools/tools.typography';
```

`sass-fonts` uses `$sf-font-type` to define if your project will be using Google Fonts or Web Fonts.

**Google Fonts**

```scss
$sf-font-type: 'googlefonts';
```

**Web Fonts**

```scss
$sf-font-type: 'webfonts';
```

**settings.fonts.scss**

```scss
$sf-font-type: 'google-fonts';  // or webfonts

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
```

**settings.typography.scss**

```scss
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
```

or if you prefer not to use `inuit-font-size` or define typographies for different breakpoints, you can manually include font-family using either one of the following mixins:

**Google Fonts**

```scss
h1 {
  @include sf-google-fonts('overpass-mono'); or // @include sf-google-fonts('overpass-mono', 'bold');
}
```

**Webfonts**

```scss
h1 {
  @include sf-webfonts('avenir-black');
}
```

## Options for Google Font `$weight` includes

- thin
- extra-light
- light
- regular (default)
- medium
- semi-bold
- bold
- extra-bold
- black

## Something not right?
Create a [Pull Request](https://github.com/xavianaxw/sass-fonts/compare) or submit an [issue](https://github.com/xavianaxw/sass-fonts/issues/new) so I can fix them!