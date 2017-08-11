# Face alignment using OpenCV

[![Build Status](https://travis-ci.org/pages-themes/hacker.svg?branch=master)](https://travis-ci.org/pages-themes/hacker) [![Gem Version](https://badge.fury.io/rb/jekyll-theme-hacker.svg)](https://badge.fury.io/rb/jekyll-theme-hacker)

* Face alignment is a computer vision technology for identifying the geometric structure of human faces in digital images. Given the location and size of a face, it automatically determines the shape of the face components such as eyes and nose.

The main aim of the project is an implementation of an excellent paper from this year's Computer Vision and Pattern Recognition Conference: One Millisecond Face Alignment with an Ensemble of Regression Trees by Vahid Kazemi and Josephine Sullivan

All discussion regarding the project can be found at opencv face alignment slack channel:

https://open-cv.slack.com/messages/C5HGCM4PR/

I have tried to provide this functionality to OpenCV. This is a tutorial describing how to use it.
[use it today](#usage). 

![Thumbnail of hacker](facereg.jpg)

## Usage

The face alignment functionality is provided in OpenCV contrib. 
To use this you have to download and install OpenCV and build it along with contrib modules.
Follow this link to install OpenCV along with OpenCV contrib.
http://docs.opencv.org/trunk/d7/d9f/tutorial_linux_install.html
## Customizing

### Configuration variables

Hacker will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```yml
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```

### Stylesheet

If you'd like to add your own custom styles:

1. Create a file called `/assets/css/style.scss` in your site
2. Add the following content to the top of the file, exactly as shown:
    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```
3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

### Layouts

If you'd like to change the theme's HTML layout:

1. [Copy the original template](https://github.com/pages-themes/hacker/blob/master/_layouts/default.html) from the theme's repository<br />(*Pro-tip: click "raw" to make copying easier*)
2. Create a file called `/_layouts/default.html` in your site
3. Paste the default layout content copied in the first step
4. Customize the layout as you'd like

## Roadmap

See the [open issues](https://github.com/pages-themes/hacker/issues) for a list of proposed features (and known issues).

## Project philosophy

The Hacker theme is intended to make it quick and easy for GitHub Pages users to create their first (or 100th) website. The theme should meet the vast majority of users' needs out of the box, erring on the side of simplicity rather than flexibility, and provide users the opportunity to opt-in to additional complexity if they have specific needs or wish to further customize their experience (such as adding custom CSS or modifying the default layout). It should also look great, but that goes without saying.

## Contributing

Interested in contributing to Hacker? We'd love your help. Hacker is an open source project, built one contribution at a time by users like you. See [the CONTRIBUTING file](CONTRIBUTING.md) for instructions on how to contribute.

### Previewing the theme locally

If you'd like to preview the theme locally (for example, in the process of proposing a change):

1. Clone down the theme's repository (`git clone https://github.com/pages-themes/hacker`)
2. `cd` into the theme's directory
3. Run `script/bootstrap` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme

### Running tests

The theme contains a minimal test suite, to ensure a site with the theme would build successfully. To run the tests, simply run `script/cibuild`. You'll need to run `script/bootstrap` one before the test script will work.
