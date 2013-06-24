# Lime SMTP Specification

This is a draft specification that defines a common structure for the
information interchanged between SMTP clients and servers from Clojure
programs.

## Definitions

The following is a breakdown of the structures that this specification
governs.

### Envelope

An envelope is a map that contains information that allows a client to
hand off a message to a server with basic SMTP.

* `:client-host`

* `:server-host`

* `:server-port`

* `:sender` - The email address that the message was sent from. This
  is different than the "From" header because the sender may not be
  the one who wrote the message, and a message can be from multiple
  email addresses.

* `:recipients` - A sequence of email addresses that the message in
  intended to be sent to. A client must generate a RCPT command for
  each recipient, and a server will collect the recipients in the
  order given.

* `:message` - A map that represents the entire message. See "Message"
  for how it is broken down.

### Message

A message is a map that represents its headers and body.

* `:headers` - A sequence of all the top-level headers on the message.
  The reason headers are represented as a sequence is because they
  must remain in order, and the same header can appear multiple times
  with different values. See "Header" for how a header is broken down.

* `:body`

### Header

A header is a map that represents a message header.

* `:name` - A string that represents the exact name of the header.

* `:value` - The unfolded string value of the header.

### Extensions

SMTP extensions augment the core definitions and are likely to affect
the behavior of the client or server. These definitions are about the
data the extensions process, and not how the extensions are
configured.

## Implementation Guide

It is important to note that the structures defined in this
specification are minimal on purpose. There is nothing wrong with a
client that provides a special key for a specific header as long as
the client ultimately puts that header into the header sequence. This
could be done by configuring the client to know about it, or before
anything is handed off to it. The same goes for a server, which can
pull a header out into its own key and do what it wants with it.
