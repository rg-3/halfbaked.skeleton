# halfbaked.skeleton

**Table of contents**

* <a href='#introduction'>Introduction</a>
* <a href='#goals'>Goals</a>
* <a href='#overview'>Overview</a>
* <a href='#file-layout'>File layout</a>
* <a href='#file-layout-visual'>File layout (visual)</a>
* <a href='#install'>Install</a>
* <a href='#source'>Source</a>


## <a id='introduction'>Introduction</a>

This repository is intended as an aid in Chrome extension development.
It provides a skeleton you can use to kickstart development of a new
extension that includes a browser action popup and a background page.

## <a id='goals'>Goals</a>

The end goal is to create a number of skeletons that target different types
of Chrome extensions, for example those who only use content scripts all the way
to those who have content scripts, a background page, and a browser action. Or
different combinations of all three.

I hope to provide skeletons that have an option to use webpack and other build tools
as well as having skeletons that do not use them, and for that to be a feature
because that model of development can be simpler.

## <a id='overview'>Overview</a>

* This skeleton is designed for an extension that has a browser action popup
  and a background page.

* This skeleton follows a model where the extension doesn't need to be "built".
  The source HTML, CSS and JS files are not processed by build tools in anyway.
  This approach provides simplicity. For example, in this environment you can
  edit the source and see the changes in the browser without a build step in
  between.

* The src/ directory is where extension code lives. The [`src/manifest.json`](src/manifest.json)
  file should be one of the first files you edit to tailor it to your project.
  Anywhere you see `EDITME` should be updated. The provided manifest.json file
  fills in the bare minimum. The [manifest.json documentation from Google](https://developer.chrome.com/extensions/manifest)
  provides a complete list of what's available.

* An objective of this skeleton is to be loadable without edits
  being made. You can try loading it in Chrome first (with Developer Mode turned on),
  then edit afterwards if you want. This allows writing code before you decide
  a project name or which icons you'll use.

## <a id='file-layout'> File layout </a>

**HTML**

* The [`src/html`](/src/html) directory contains [`browser-action.html`](src/html/browser-action.html) and
  [`background.html`](src/html/background.html).

* The [`src/html/browser-action.html`](src/html/browser-action.html) file can be edited to change
  the contents of the browser action's popup.

* The [`src/html/background.html`](src/html/background.html) file's main purpose is to include
  [`src/js/background.js`](/src/js/background.js).

**CSS**

* The [`src/css/`](/src/css) directory is for CSS belonging to your extension.

* The [`src/css/browser-action.css`](/src/css/browser-action.css) file styles the content of 
  [`src/html/browser-action.html`](/src/html/browser-action.html).

**JavaScript**

 * The [`src/js/`](/src/js) directory is for JavaScript belonging to your extension.

 * The [`src/js/browser-action/`](src/js/browser-action) directory is for JavaScript
   that's unique to the browser action popup.

  * The [`src/js/background/`](src/js/background) directory is for JavaScript
    belonging to your extension's background page.

 * The [`src/js/background.js`](src/js/background.js) file is implemented to
   define `window.app`.  
   The `app` object is created by importing and instantiating 
   [`src/js/background/app.js`](src/js/background/app.js).

   **Tip**  
   The background page is instantiated once each time the browser starts. It provides 
   a layer of persistence while its in memory and we can also avail of its other 
   features such as `window.localStorage`.

 * The [`src/js/browser-action.js`](src/js/browser-action.js) file is included
   by [src/html/browser-action.html](src/html/browser-action.html) every time 
   the browser action's popup is opened.

   **Tip**  
   The `app` object implemented by the background page can be accessed from the
   browser action with this code: 
   
        chrome.extension.getBackgroundPage().app


**Images**

* The [`src/images`](src/images) directory is for images used by your extension.

## <a id='file-layout-visual'>File layout (visual)</a>

    $ tree
    .
    ├── README.md
    └── src
        ├── css
        │   └── browser-action.css
        ├── html
        │   ├── background.html
        │   └── browser-action.html
        ├── images
        │   ├── icon128.png
        │   ├── icon16.png
        │   └── icon48.png
        ├── js
        │   ├── background
        │   │   └── app.js
        │   ├── background.js
        │   ├── browser-action
        │   └── browser-action.js
        ├── LICENSE.txt
        └── manifest.json

    7 directories, 12 files


## <a id='install'> Install </a>

The install process is simple. All you have to do is clone the project and
then adopt it as the starting point for your new extension.

    git clone https://github.com/rg-3/halfbaked.skeleton my-project-name
    cd my-project-name
    # Make room for your own repository
    rm -rf .git
    # Make room for your own README
    mv README.md README.skeleton.md


## <a id='source'>Source</a>

The project homepage for this skeleton is at [https://github.com/rg-3/halfbaked.skeleton](https://github.com/rg-3/halfbaked.skeleton).
I am maintaining other Chrome extension skeletons that might be helpful on my [github profile](https://github.com/rg-3).
