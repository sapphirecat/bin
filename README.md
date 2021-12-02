# bin

Random personal scripts that may be helpful


## activate

Perl script to activate a virtualenv, given a project name.  Searches, by
order of precedence, a path specified with `--path=PATHSPEC` on the command
line, the `$ACTIVATE_PATH` environment variable, or a built-in default of
`~/git` if neither of the above are set.

The project’s `bin` directory will be checked (unless `--no-bin` is
specified), then the project’s root folder.  The first script found wins.

`activate` _should_ work on Windows, but hasn’t actually been tested there.
There is an option to specify the executable extension, that defaults to
“.bat” on Windows or empty elsewhere.  This can be changed with e.g.
`--ext=.exe` to search for and invoke `activate.exe` instead.

The repository includes a sample “activate project” script for use with Perl
projects on POSIX systems; it’s called `_activate-project` and, somewhat
confusingly, should be installed inside the project being activated.  In other
words:

    cd THIS_REPO
    cp -p _activate-project ~/git/foo/activate
    ./activate foo

This will (using the default paths) activate the project foo.  If you have a
`~/lib/foo` directory, then it will be added to the environment as a
`local::lib` path.  (I use this last feature to evaluate CPAN modules without
polluting a ‘real’ installation.)

`_activate-project` should be customized for your needs; for instance, to
change your shell prompt to indicate that you’re inside the project.


## perl\_has

Shows whether the Perl modules named on the command line are available in the
current installation.  Example:

    perl_has Date::Parse LWP::UserAgent

## randbits

Generates keys from `/dev/random`, and prints their base64 encoding.

# License

All scripts are GPL v3 or later.
