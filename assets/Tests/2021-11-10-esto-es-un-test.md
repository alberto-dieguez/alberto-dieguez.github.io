---
title: Probando
author:
  name: Cotes Chung
  link: https://github.com/cotes2020
date: 2021-11-10 02:25:00 +0100
categories: [Blogging, Tutorial]
tags: [favicon]
img:
---

The [favicons](https://www.favicon-generator.org/about/) of [**Chirpy**](https://github.com/cotes2020/jekyll-theme-chirpy/) are placed in the directory `assets/img/favicons/`. You may want to replace them with your own. The following sections will guide you to create and replace the default favicons.

# H1
## H2
### H3
#### H4

## Generate the favicon

Prepare a square image (PNG, JPG, or SVG) with a size of 512x512 or more, and then go to the online tool [**Real Favicon Generator**](https://realfavicongenerator.net/) and click the button <kbd>Select your Favicon image</kbd> to upload your image file.

In the next step, the webpage will show all usage scenarios. You can keep the default options, scroll to the bottom of the page, and click the button <kbd>Generate your Favicons and HTML code</kbd> to generate the favicon.

## Download & Replace

Download the generated package, unzip and delete the following two from the extracted files:

- `browserconfig.xml`
- `site.webmanifest`

Now, copy the remaining image files (`PNG` and `ICO`) to cover the original files in the folder `assets/img/favicons/` of your Jekyll site. If your Jekyll site doesn't have this directory yet, just create one.

The following table will help you understand the changes to the favicon files:

| File(s)             | From Online Tool                  | From Chirpy |
|---------------------|:---------------------------------:|:-----------:|
| `*.PNG`             | ✓                                 | ✗           |
| `*.ICO`             | ✓                                 | ✗           |
| `browserconfig.xml` | ✗                                 | ✓           |
| `site.webmanifest`  | ✗                                 | ✓           |

> Note: ✓ means keep, ✗ means delete.

The next time you build the site, the favicon will be replaced with a customized edition.

y mas
probando cosas, 