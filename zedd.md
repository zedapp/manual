Zedd
====

Zedd is the "Zed daemon", a process that runs in the background with the sole purpose of making your local or remote file system available for editing in Zed. In addition, it enables Zed features that are not easy/impossible to implement using regular Chrome APIs, such as running external programs. It also makes working with files on remote servers more convenient and flexible.

**Use of Zedd is optional. You can use most features of Zed just fine without Zedd.**

So why would you install Zedd, then?

**For Zed Chrome App users:** The advantage of using Zedd instead of using the "Local Folder" project type is the ability to run external programs from the editor, such as linters, build tools or git tools. Various Zed packages and commands that require this feature will only be available in Zedd projects.

**For Zed standalone users:** Running Zedd locally is not particularly useful. Don't bother. Unless you edit files remotely...

**For Zed users editing files remotely:** If you edit a lot of files remotely on a server, you can run Zedd in remote mode. What this will give you over zedrem ([remote]) is:

1. It's safe to keep Zedd running in the background, you can enable SSL and authentication. Zedd projects also appear in your recent projects lists, so they're easy to get back to.
2. You can enable running of external programs on your server, like linters, build tools, git etc. Note that you have to enable this feature explicitly (for security reasons).
3. Zedd doesn't depend on a central server -- connections from Zed are made directly to your server running Zedd, so you're not dependent on some server we maintain.


Installation
---------
Zedd is installed using NPM, the node package manager. If you do not have npm installed, you need to install that first. Then, install Zedd as follows:

    sudo npm install -g zedd

After successful installation you start zedd simply by running:

    zedd

If you don't have root access on the machine where you're installing zedd, you can also run:

    npm install zedd

And subsequently run it using:

    ./node_modules/.bin/zedd

Either way, by default, this will expose your user's home directory (`$HOME`) via http://127.0.0.1:7337. However, when you close your terminal window or hit Ctrl-C zedd will quit. Ideally, you keep Zedd running at all times, one way to do this on Unix systems is using:

    nohup zedd &

However, after you reboot your machine you have to run this command again.

Running Zedd using supervisord
------

Alternatively, you can use a process manager like supervisord to automatically start zedd on boot and keep it running while your system is up.

Installing supervisord differs on a per-platform basis. On Ubuntu Linux you install it using:

    sudo apt-get install supervisor

After installing supervisord, and making sure it boots when your system boots, you can now create a process configuration file under (usually) `/etc/supervisor/conf.d`, we'll call this file `/etc/supervisor/conf.d/zedd.conf`. In its most basic form, this will will contain:

    [program:zedd]
    command=zedd
    user=YOURUSER

Replace YOURUSER with your Unix username. Zedd will run under this user. To start zedd:

    sudo supervisorctl reload

Verify it's running correctly using:

    sudo supervisorctl status

Using Zedd
----------
In the Zed project picker select "Zedd Folder", then fill in the URL to your Zedd server in the URL box, e.g. http://localhost:7337 authentication is disabled by default, which is ok since nobody from outside your machine can access this server. After pressing "Connect" you will see a directory tree, from which you can select the folder to edit.

Zedd options
---------
Zedd takes a number of command-line arguments. At the time of this writing:

    $ zedd --help
    Zedd is the Zed daemon used to edit files either locally or remotely using Zed.
    Options can be passed in either as environment variables, JSON config in
    ~/.zeddrc or as command line arguments prefixed with '--':

       user:       username to use for authentication (default: none)
       pass:       password to use for authentication (default: none)
       remote:     bind to 0.0.0.0, requires auth, and disables
                   enable-run by default
       port:       port to bind to (default: 7337)
       root:       root directory to expose (default: $HOME)
       enable-run: enable running of external programs in remote mode
       tls-key:    path to TLS key file (enables https)
       tls-cert:   path to TLS certificate file (enables https)


By default authentication is disabled, and only your home directory is accessible. To expose your entire disk, you can pass the `--root` directory. To set up a username and password for authentication, you can pass `--user` and `--pass`:

    zed --root / --user me --pass letmein

Running Zedd in remote mode
--------------

If you often edit files on a remote server, or subscribe to the idea of a "cloud development environment". You can run zedd on that server in remote mode using the `--remote` option. What this will do is:

* Bind to IP `0.0.0.0` meaning outside connections will be accepted.
* Disable running of external programs by default, you can re-enable this feature using the `--enable-run` flag.
* Require that you use pass in `--user` and `--pass` flags, otherwise your system would be wide open for random reads and writes of the exposed file system.

Other suggested options in remote mode are the `--tls-key` and `--tls-cert` arguments (they take a path to an openssl key and certificate, respectively), which switches zedd to run over `https` rather than plain `http`. Obviously, you will need a SSL certificate for this.

You connect to a remote zedd server the same way as a local one, except that you use the IP (or host name) of the server instead of 127.0.0.1.
