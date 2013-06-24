# Lime SMTP Specification

This project contains the draft specification for the SMTP API. This
specification is currently supported by the [Lime SMTP Client][c] and
[Lime SMTP Server][s] projects, however other projects are welcome to
support it as well.

## Purpose

The purpose of this specification is to provide a common structure for
the information interchanged between SMTP clients and servers within
Clojure programs. The specification mentions some serialization and
deserialization rules to maintain the integrity of the certain pieces
information. However, those rules are kept to a minimum to let
implementers decide what is best for their programs.

## Contributions

Anyone may contribute to the specification. Please open an issue or a
pull request with your thoughts.

[c]: https://github.com/limemail/lime.smtp.client "Lime SMTP Client"
[s]: https://github.com/limemail/lime.smtp.server "Lime SMTP Server"
