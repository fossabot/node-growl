# Growl for Node.js

[![Build Status][Travis-NodeGrowl-badge]][Travis-NodeGrowl]
[![Dependency Status][David-NodeGrowlDep-badge]][David-NodeGrowlDep]
[![devDependency Status][David-NodeGrowlDevDep-badge]][David-NodeGrowlDevDep]

This is essentially a port of my [Ruby Growl Library][].
Ubuntu/Linux support added thanks to [@niftylettuce][].

[![NPM][NPM-NodeGrowl-badge]][NPM-NodeGrowl]

## Installation

### Mac OS X (Darwin):

  Install [growlnotify(mac)][]. On OS X 10.8, Notification Center is supported using [terminal-notifier][]. To install:

    $ sudo gem install terminal-notifier

  Install [npm][] and run:

    $ npm install growl

### Ubuntu (Linux):

  Install `notify-send` through the [libnotify-bin][] package:

    $ sudo apt-get install libnotify-bin

  Install [npm][] and run:

    $ npm install growl

### Windows:

  Download and install [Growl for Windows][]

  Download [growlnotify(win)][] - **IMPORTANT :** Unpack growlnotify to a folder that is present in your path!

  Install [npm][] and run:

    $ npm install growl

## Examples

Callback functions are optional

```javascript
var growl = require('growl')
growl('You have mail!')
growl('5 new messages', { sticky: true })
growl('5 new emails', { title: 'Email Client', image: 'Safari', sticky: true })
growl('Message with title', { title: 'Title'})
growl('Set priority', { priority: 2 })
growl('Show Safari icon', { image: 'Safari' })
growl('Show icon', { image: 'path/to/icon.icns' })
growl('Show image', { image: 'path/to/my.image.png' })
growl('Show png filesystem icon', { image: 'png' })
growl('Show pdf filesystem icon', { image: 'article.pdf' })
growl('Show pdf filesystem icon', { image: 'article.pdf' }, function(err){
  // ... notified
})
```

## Options

  - title
    - notification title
  - name
    - application name
  - priority
    - priority for the notification (default is 0)
  - sticky
    - weither or not the notification should remainin until closed
  - image
    - Auto-detects the context:
      - path to an icon sets --iconpath
      - path to an image sets --image
      - capitalized word sets --appIcon
      - filename uses extname as --icon
      - otherwise treated as --icon
  - exec
    - manually specify a shell command instead
      - appends message to end of shell command
      - or, replaces `%s` with message
      - optionally prepends title (example: `title: message`)
      - examples: `{exec: 'tmux display-message'}`, `{exec: 'echo "%s" > messages.log}`

[//]: # (Cross reference section)

[Ruby Growl Library]: https://github.com/visionmedia/growl/
[@niftylettuce]: https://github.com/niftylettuce/
[npm]: https://npmjs.org/
[terminal-notifier]: https://github.com/alloy/terminal-notifier/
[libnotify-bin]: https://packages.ubuntu.com/trusty/libnotify-bin
[Growl for Windows]: http://www.growlforwindows.com/gfw/default.aspx
[growlnotify(mac)]: http://growl.info/extras.php#growlnotify
[growlnotify(win)]: http://www.growlforwindows.com/gfw/help/growlnotify.aspx

[Travis-NodeGrowl]: https://travis-ci.org/tj/node-growl/
[Travis-NodeGrowl-badge]: https://travis-ci.org/tj/node-growl.svg?branch=master
[David-NodeGrowlDep]: https://david-dm.org/tj/node-growl/
[David-NodeGrowlDep-badge]: https://david-dm.org/tj/node-growl/status.svg
[David-NodeGrowlDevDep]: https://david-dm.org/tj/node-growl/?type=dev
[David-NodeGrowlDevDep-badge]: https://david-dm.org/tj/node-growl/dev-status.svg
[NPM-NodeGrowl]: https://npmjs.org/package/node-growl/
[NPM-NodeGrowl-badge]: https://nodei.co/npm/node-growl.png?downloads=true&downloadRank=true&stars=true

