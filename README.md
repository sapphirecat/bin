# bin

Random personal scripts that may be helpful

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

All scripts are GPL v3 only.
