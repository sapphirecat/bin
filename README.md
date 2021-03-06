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


## \_vmconnect

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

Version 1.2.0-dev and later offer control over some defaults through the
environment, rather than hard-coding them into the script:

    VMCONNECT_VM          - VirtualBox VM name to start
    VMCONNECT_START_AGENT - non-empty to start a fresh SSH agent
    VMCONNECT_SSH_KEY     - key to load into the/an agent
    VMCONNECT_INIT_WAIT   - steps to wait for a VM to boot
    VMCONNECT_SSH_WAIT    - steps to wait for ssh to connect
    VMCONNECT_STEP        - delay between init/ssh countdown

Defaults are “ubuntu” VM, and no agent/key operations.  The default step is 2,
which means that the default init wait of 6 allows 12 seconds for a VM to boot
before trying to connect, and the default ssh wait of 30 will wait 60 (more)
seconds for the VM to become reachable.

# License

All scripts are GPL v3 or later.
