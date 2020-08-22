# content-script.skeleton

**Table of contents**

* <a href='#introduction'>Introduction</a>
* <a href='#approach'>The approach this skeleton takes</a>
* <a href='#install'>Install</a>

## <a id='introduction'>Introduction</a>

This repository is intended as an aid in Chrome extension development.
It provides a skeleton you can use to kickstart development of a new
extension who has a focus on content scripts.

It's my intention to create a number of skeletons that target different types
of Chrome extensions, for example those who only use content scripts all the way
to those who have content scripts, a background page and a browser action.

This particular skeleton targets extensions who only inject content scripts
onto web page(s). A familiarity with extension development is assumed.

## <a id='approach'>The approach this skeleton takes</a>

* This skeleton follows a model where the extension doesn't need to be "built".
  The source HTML, CSS and JS files are not processed by build tools in anyway.
  This approach provides simplicity. For example, in this environment you can
  edit the source and see the changes in the browser without a build step in
  between.

* The `src/` directory is where extension code lives. The `src/manifest.json`
  file should be one of the first files you edit to tailor it to your project.
  Anywhere you see `EDITME` should be updated.

* This skeleton is designed for an extension that injects content scripts
  onto web page(s). It doesn't provide for anything beyond that like setting
  up the extension to have a browser action, or background page.

* The `src/js` directory holds another directory named `content-scripts`. Inside
  this directory content scripts should be placed and further configured in
  `src/manifest.json`. `src/js/content-scripts/content-script.js` is
  provided as a starting point for a content script that can be edited and
  renamed.

* The `src/images` directory holds placeholder icons that the browser will
  display alongside the address bar and on the `chrome://extensions` page.
  Most likely you will eventually want to update these for your own extension.

* An objective of this skeleton is to be loadable without edits
  being made. You can try loading it in Chrome first (with Developer Mode turned on),
  then edit afterwards if you want.

## <a id='install'> Install </a>

The install process is simple. All you have to do is clone the project and
then edit it to meet your needs.

    git clone https://github.com/rg-3/content-script.skeleton my-project-name

