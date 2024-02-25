<!-- https://jekyllrb.com/docs/front-matter/ -->

# Layouts

Any file that contains a YAML front matter block will be processed by Jekyll as a special file.

The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. Here is a basic example:

```css
---
layout: post
title: Blogging Like a Hacker
---
```

Between these triple-dashed lines, you can set predefined variables (see below for a reference) or even create custom ones of your own. These variables will then be available for you to access using Liquid tags both further down in the file and also in any layouts or includes that the page or post in question relies on.

## Variables

`layout`

If set, this specifies the layout file to use. Use the layout file name without the file extension. Layout files must be placed in the _layouts directory.
