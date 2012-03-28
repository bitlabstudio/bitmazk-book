GNU Screen
==========

* open new screen session
  screen -d -R name
* CTRL+A w --> show open tabs
* CTRL+A c --> open new tab
* CTRL+A :title foobar --> set tab title
* CTRL+A 0-9 --> jump between tabs
* CTRL+A :quit --> terminate session
* exit into shell --> exit screen tab, terminates session when exiting last tab
* CTRL+A ? --> show help
* CTRL+A :multiuser on --> enable multiuser mode
* screen -xr sessionname --> attach to running multiuser session
