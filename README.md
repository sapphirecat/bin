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

## perl_has

Shows whether the Perl modules named on the command line are available in the
current installation.  Example:

    perl_has Date::Parse LWP::UserAgent

## _vmconnect

Connects to a VirtualBox guest.  If the guest isn’t running, it will be
started headlessly.

Best used as the “session command” of your terminal emulator; e.g. for my
iTerm2 “dev” profile, I set the Command to `/path/to/_vmconnect dev`.  Now I
can fearlessly open that profile without needing to use any VirtualBox UI, or
even make sure the guest is running.

Of course, there’s also a port forwarded to the VM, and I added a block to
`~/.ssh/config` so I can connect there with a simple `ssh dev`:

    Host dev
    HostName 127.0.0.1
    Port 9222
    User ubuntu

# License

All scripts are GPL v3 or later.
