# *endl* (Link Extractor and Downloader) [![Build Status](https://travis-ci.org/dogancelik/endl.svg?branch=master)](https://travis-ci.org/dogancelik/endl)
A Node.js module for extracting links from web pages and downloading them.

[![NPM](https://nodei.co/npm/endl.png?downloads=true&stars=true)](https://nodei.co/npm/endl/)

*endl* has a very simple also an advanced API for link extracting, file downloading, executing and unzipping.

**Every version under 1.0 is beta. This means it has bugs and features can change.**

## Simple example
This is written in [*CoffeeScript*](https://github.com/jashkenas/coffeescript).

```coffee
endl = require 'endl'

endl.page('http://lame.buanzo.org/')
  .find('a[href^="http://lame.buanzo.org/Lame_"]')
  .download(pageUrlAsReferrer: true, filenameMode: { urlBasename: true })
```

[More examples here](https://github.com/dogancelik/endl/wiki/Examples)

### Explanation
1. We *require* our *endl* module.
2. `endl.page()` loads the page we want. (It takes two arguments, second argument is an options *object* and optional.)
3. `find()` finds the elements we want. (Works just like jQuery and querySelectorAll)
4. Download our file to the current directory, using basename of our download link for file name and using our page URL as *Referer* header.

Things to note:
* We actually get 4 elements when we do `find()` but `download()` automatically selects the first element (0-index). Use `index()` to change index of element array.
* `download()` after `find()` is a shortcut. The long way is: *find(...)* → *href()* → *download(...)*

## Latest breaking changes
* Removed CSON in *v0.3.0*
* Changed `endl.load()` to `endl.page()` in *v0.2.0*
* Changed `endl.parse()` to `endl.load()` in *v0.2.0*
* Changed download option `fileDirectory` to `directory` in *v0.2.0*

## How to install?
[![NPM](https://nodei.co/npm/endl.png?mini=true)](https://nodei.co/npm/endl/)

Prerequisites: Tools for building NodeJS native modules

## How do you pronounce *endl*?
Like *Handel* the composer, but without the *h* → *andel* :)

## Current issues
* findXpath doesn't work. Blame web pages (for incorrect structure), xmldom and xpath modules.

## To-Do
* Unify all downloading, extraction and execution options across submodules. (`endl.coffee`, `file.coffee`, `parser.coffee`) These 3 submodules have different *default* options for each task.
* Add more tests.
* Turn every blocking function into async (I'm using deasync in some places)

### Command Line
See [*endl-cli*](https://github.com/dogancelik/endl-cli)

## API
[Go to API page](https://github.com/dogancelik/endl/wiki/API)
