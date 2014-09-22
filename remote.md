Editing Remote Files with Zed
=============================

Zed has excellent support for editing files living on remote servers. This even works for servers behind firewalls or living on a VPN, as long as the server can make outbound connections to the Internet.

To use this feature, you need to install `zedrem` on the server where files are to be edited. On most Unixes (e.g. Linux, Mac OS X and FreeBSD) installing the `zedrem` program is as easy as:

    curl http://get.zedapp.org | bash

For Windows download the [Zed client](http://get.zedapp.org/zed.exe).

Then, you have two options. The simplest option (if you don't use zedrem often), is to simply run zedrem as follows:

    ./zedrem <directory-to-edit>

This will give you a URL you need to copy and paste the "Remote Folder" option in the Zed project picker (this screen also explains the steps above). To stop editing, close the window and kill the Zed binary on the server with Ctrl-C.

The second option is to pass in your user-specific "zedrem key" when running zedrem. You can obtain this key by running the `Configuration:Zedrem:Get User Key` command (or looking in your `/user.json` file in your Configuration project under preferences / zedrem / userKey). Then, run zedrem as follows:

    ./zedrem -key yourkeyhere <directory-to-edit>

If you run zedrem this way, a Zed window editing the files in this directory will automaticaly pop up, so you don't have to copy & paste anything.

If you want to override default options like the zedrem server to connect to or the default userkey to use (useful when editing files on the same server a lot), you can add these to your ~/.zedremrc file (create it if it doesn't exist), for instance:

    [client]
    url = wss://remote.zedapp.org:443
    userKey = CC8E841A2E234F23B9065E904CFAD912

When configured this way, you can run zedrem without flags and still have editor windows pop up automatically.
