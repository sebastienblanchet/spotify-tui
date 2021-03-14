## Requirements

### Client

* use wasm (yew), port from tui


### Server

* read audio file from spotifyd/ audio analysis
* extract frequency spectrum/EQ chart
* take a list of modifications
* read new audio
* extract drum info
* send array of [kick, tom, snare, overhead, hithat] in REALTIME
* GPIO LED
  * https://github.com/golemparts/rppal#gpio
