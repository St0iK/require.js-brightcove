# Loading the Brightcove Player with Require.js

## What?
Brightcove player detects if require.js is already loaded and registers the player as a module ('bc').
As a result the global objects that the player registers (bc, videojs) are not immidiatelly availiable.

This is a proof of concept to see if we can load the player and make these functions availiable globally.

Codepen: https://codepen.io/st0ik/pen/eYNYPev?editors=1010


### Brighcove Player checks

https://players.brightcove.net/1507807800001/default_default/index.min.js
```
(function(e, t) {
    if (typeof define === "function" && define.amd) {
        define("bc", [], function() {
            var i = t.apply(this, arguments);
            e.videojs.log.warn("DEPRECATION: Using the default named RequireJS module in the Brightcove Player is deprecated. See: https://support.brightcove.com/requirejs-and-brightcove-player#Future_implementation");
            return i
        })
    } else if (typeof exports === "object") {
        module.exports = t()
    } else {
        e.bc = t(e)
    }
})
```


### RequireJS and Brightcove Player

https://support.brightcove.com/requirejs-and-brightcove-player


```
require(['bc'], function() {
      var myPlayer = videojs.getPlayers().myPlayerID;
      myPlayer.on('loadstart', function(){
        myPlayer.play();
      })
    });
```