# nscreen bash bundle

Provides easy access to named screens with autocompletion of running sessions, as well as optional screen configs on a per-name basis, with the main ~/.screenrc being merged with the topic config

# Usage

	nscreen mysessionname

Opens a new screen session with the given name. As long as the session is alive, the same command will now attach to the session (detaching it from the previously attached terminal)

# Topic configs

If you create a file ~/.screen-<name>, upon creation of a named session of the same name, nscreen will concatenate your ~/.screenrc and ~/.screen-<name> file, store it as ~/.nscreen-<md5>, and start screen with this file as its config file.

This way, you may preconfigure a bunch of ssh sessions, like loadbalancer or database failover pairs, a bunch of slave databases of a common master etc.

	zombie k
	screen ssh databasenode1
	screen ssh databasenode2

zombie k will make screen not close a window when the ssh session disconnects, and ask you to hit k to really close the window or CTRL-Space to reopen the ssh session.
