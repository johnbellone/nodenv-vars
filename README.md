# nodenv-vars

This is a plugin for [nodenv](https://github.com/OiNutter/nodenv)
that lets you set global and project-specific environment variables
before spawning Node processes.

## Installation

To install nodenv-vars, clone this repository into your
`~/.nodenv/plugins` directory. (You'll need a recent version of nodenv
that supports plugin bundles.)

    $ mkdir -p ~/.nodenv/plugins
    $ cd ~/.nodenv/plugins
    $ git clone https://github.com/johnbellone/nodenv-vars.git

## Usage

Define environment variables in an `.nodenv-vars` file in your project,
one variable per line, in the format `VAR=value`. For example:

You may also have conditional variable assignments, such that a
variable will **only** be set if it is not already defined or is blank:

    JAVA_OPTS?=-server -Xmx768m -Xms768m -Xmn128m -Xss20m

In the above case, `JAVA_OPTS` will only be set if `$JAVA_OPTS` is
currently empty (i.e., if `[ -z "$JAVA_OPTS" ]` is true).

Spaces are allowed in values; quoting is not necessary. Expansion and
command substitution are not allowed. Lines beginning with `#` or any
lines not in the format VAR=value will be ignored.

Variables specified in the `~/.nodenv/vars` file will be set
first. Then variables specified in `.nodenv-vars` files in any parent
directories of the current directory will be set. Variables from the
`.nodenv-vars` file in the current directory are set last.

Use the `nodenv vars` command to print all environment variables in the
order they'll be set.

## Version History

**1.0.0** (October 28th, 2013)

* Initial public release.

## License

&copy; 2012 Sam Stephenson.

&copy; 2013 Bloomberg L.P. Released under the MIT license. See
`LICENSE` for details.
