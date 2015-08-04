SerWebProxy is a GPL multi-threaded proxy program for redirecting
network socket connections to/from serial links, in cases where
the remote end of the serial link doesn't have a TCP/IP
stack (eg an embedded or microcontroller system).

The proxy allows other hosts on the network to communicate
with the system on the remote end of the serial link.
When run, it listens for incoming connections on a specified TCP
ports. Whenever a connection is made data is proxied to and from
that connection to a serial port.

To control serial device from browser, there are two protocol available :

  * WebSocket protocol (spec 10)
  * HTTP GET
  * raw TCP socket (no browser support, for other purposes)

WebSocket works as expected, connection is kept open and it's very similar to
how serial ports work. However, HTTP GET request is one-way and single request
type of communication. SerWebProxy handles it so that when GET request is made,
parameters (everything after hostname) are sent to serial port and response is
read until end of line appears. Then data is sent to network and connection is
closed.

Example GET request to make from browser could be 'http://localhost:5331/hello'
and serial device would then receive hello.

Tested with Linux and Windows. See readme for more information.