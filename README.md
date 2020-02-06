# Loading the Brightcove Player with Require.js

## What?
Brightcove player detects if require.js is already loaded and registers the player as a module ('bc').
As a result the global objects that the player registers (bc, videojs) are not immidiatelly availiable.

This is a proof of concept to see if we can load the player and make these functions availiable globally.

Codepen: https://codepen.io/st0ik/pen/eYNYPev?editors=1010