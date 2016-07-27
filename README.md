# rubyserial

RubySerial is a simple Ruby gem for reading from and writing to serial ports.

Unlike other Ruby serial port implementations, it supports all of the most popular Ruby implementations (MRI, JRuby, & Rubinius) on the most popular operating systems (OSX, Linux, & Windows). And it does not require any native compilation thanks to using RubyFFI [https://github.com/ffi/ffi](https://github.com/ffi/ffi).

The interface to RubySerial should be (mostly) compatible with other Ruby serialport gems, so you should be able to drop in the new gem, change the `require` and use it as a replacement. If not, please let us know so we can address any issues.

[![Build Status](https://travis-ci.org/hybridgroup/rubyserial.svg)](https://travis-ci.org/hybridgroup/rubyserial)
[![Build status](https://ci.appveyor.com/api/projects/status/946nlaqy4443vb99/branch/master?svg=true)](https://ci.appveyor.com/project/zankich/rubyserial/branch/master)
[![Test Coverage](https://codeclimate.com/github/hybridgroup/rubyserial/badges/coverage.svg)](https://codeclimate.com/github/hybridgroup/rubyserial/coverage)

## Installation

    $ gem install rubyserial

## Usage

```ruby
require 'rubyserial'
serialport = Serial.new '/dev/ttyACM0' # Defaults to 9600 baud, 8 data bits, and no parity
serialport = Serial.new '/dev/ttyACM0', 57600
serialport = Serial.new '/dev/ttyACM0', 19200, 8, :even
```

## Methods

**write(data : String) -> Int**

Returns the number of bytes written.
Emits a `RubySerial::Exception` on error.

**read(length : Int) -> String**

Returns a string up to `length` long. It is not guaranteed to return the entire
length specified, and will return an empty string if no data is
available. Emits a `RubySerial::Exception` on error.

**getbyte -> Fixnum or nil**

Returns an 8 bit byte or nil if no data is available.
Emits a `RubySerial::Exception` on error.

**RubySerial::Exception**

A wrapper exception type, that returns the underlying system error code.

## Running the tests

The test suite is written using rspec, just use the `rspec` command.

However, to run the tests, you must also have the `socat` utility program installed.

### Installing socat on OS X

```
brew install socat
```

### Installing socat on Linux

```
sudo apt-get install socat
```

### Installing socat on Windows

You might need to build from source... the latest build of socat for Windows is quite old. Get source from here:

http://www.dest-unreach.org/socat/download/

## License

Apache 2.0. See `LICENSE` for more details.
