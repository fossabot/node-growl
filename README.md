# Growl for Node.js

[![Build Status][Travis-NodeGrowl-badge]][Travis-NodeGrowl]
[![Dependency Status][David-NodeGrowlDep-badge]][David-NodeGrowlDep]
[![devDependency Status][David-NodeGrowlDevDep-badge]][David-NodeGrowlDevDep]
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fplroebuck%2Fnode-growl.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fplroebuck%2Fnode-growl?ref=badge_shield)

This is essentially a port of my [Ruby Growl Library][].
Ubuntu/Linux support added thanks to [@niftylettuce][].

[![NPM][NPM-NodeGrowl-badge]][NPM-NodeGrowl]

## Installation

### macOS

On OS X 10.8+, Notification Center is supported via [terminal-notifier][].

```bash
$ sudo gem install terminal-notifier
$ npm install growl
```

Many years ago, the instructions would have used the original developer's
product [growlnotify (mac)][], but unsure if it still works.

### Linux

Install "notify-send" through the [libnotify-bin][] APT package. If you use
RPM packages, substitute appropriately.

```bash
$ sudo apt-get install libnotify-bin
$ npm install growl
```

### Windows

Download and install [Growl for Windows][]

Download [growlnotify (win)][] - **IMPORTANT :** Unpack "growlnotify" to a folder that is present in your **PATH**!

```posh
C:> echo %path:;=&echo.%
C:> npm install growl
```

## Getting Started

This module consists of a single exported function. Use it as follows:

```javascript
// Import the module
var growl = require('growl');

// Invoke with only the `msg` argument
growl('This is a test');

// Repeat the previous notification, adding `options.title`
growl('This is a test', { title: 'Test' });

// Repeat the previous notification, adding `callback`
growl('This is a test', { title: 'Test' }, function (error) {
  console.error('notification failed.');
  console.error(error);
});
```

## Arguments

### msg

Message to be displayed.

### options

* title
  * Notification title
* sticky
  * Should the notification should remain until closed? (default is false)
* priority
  * Priority for the notification (default is 0)
* name
  * Application name
* sound
  * Alert sound [macOS 10.8+ only]
* image
  * Auto-detects the context on macOS:
    * path to an iconset --iconpath
    * path to an image --image
    * capitalized word sets --appIcon
    * filename uses extname as --icon
    * otherwise treated as --icon
* exec
  * Manually specify a shell command instead
    * appends message to end of shell command
    * or, replaces `%s` with message
    * optionally prepends title (example: `title: message`)
    * examples:
      * `{exec: 'tmux display-message'}`
      * `{exec: 'echo "%s" > messages.log}`

### callback

Callback function is optional. If notifications are not occurring, this
can be used to troubleshoot. Its function signature is:

```js
function (error, stdout, stderr)
```

However, the latter two arguments are only used in conjunction with
`options.exec`.

## Examples

```javascript
var growl = require('growl')
growl('You have mail!')
growl('5 new messages', { sticky: true })
growl('5 new emails', { title: 'Email Client', image: 'Safari', sticky: true })
growl('Message with title', { title: 'Title'})
growl('Set priority', { priority: 2 })
growl('Play sound on macOS', { title: 'Notification Center', sound: 'Purr' })
growl('Show Safari icon', { image: 'Safari' })
growl('Show icon', { image: 'path/to/icon.icns' })
growl('Show image', { image: 'path/to/my.image.png' })
growl('Show png filesystem icon', { image: 'png' })
growl('Show pdf filesystem icon', { image: 'article.pdf' })
growl('Show pdf filesystem icon', { image: 'article.pdf' }, function(err){
  // handle error...
})
```

[//]: # (Cross reference section)

[Ruby Growl Library]: https://github.com/visionmedia/growl/
[@niftylettuce]: https://github.com/niftylettuce/
[terminal-notifier]: https://github.com/alloy/terminal-notifier/
[libnotify-bin]: https://packages.ubuntu.com/trusty/libnotify-bin
[Growl for Windows]: http://www.growlforwindows.com/gfw/default.aspx
[growlnotify (win)]: http://www.growlforwindows.com/gfw/help/growlnotify.aspx
[growlnotify (mac)]: http://growl.info/extras.php#growlnotify

[Travis-NodeGrowl]: https://travis-ci.org/tj/node-growl/
[Travis-NodeGrowl-badge]: https://travis-ci.org/tj/node-growl.svg?branch=master
[David-NodeGrowlDep]: https://david-dm.org/tj/node-growl/
[David-NodeGrowlDep-badge]: https://david-dm.org/tj/node-growl/status.svg
[David-NodeGrowlDevDep]: https://david-dm.org/tj/node-growl/?type=dev
[David-NodeGrowlDevDep-badge]: https://david-dm.org/tj/node-growl/dev-status.svg
[NPM-NodeGrowl]: https://npmjs.org/package/node-growl/
[NPM-NodeGrowl-badge]: https://nodei.co/npm/node-growl.png?downloads=true&downloadRank=true&stars=true



## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fplroebuck%2Fnode-growl.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fplroebuck%2Fnode-growl?ref=badge_large)