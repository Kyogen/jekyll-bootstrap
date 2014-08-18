---
layout: post
title:  "Serving content with lighttpd"
date:   2014-08-16 23:30:00
categories: [web, server]
---

Well, the first post is already some months old now. Blogging is not as easy
after all :)

As promised, I want to give some details about turning a [Raspberrypi][pi] into
a server for your blog (or whatever you want to show to the internet). To turn
any computer into a server, the most important piece of software is a webserver
daemon, which is a program responsible for listening on incoming requests from
the internet and delivering the content you want to serve. There are different
webserver daemons you can choose from. The biggest three (as far as I know) are
[Apache][apa], [Nginx][ng] and [lighttpd][light]. All three are available in
the Archlinux repositories. Most servers run Apache, but I think it is a bit
overblown for delivering some static content like a blog, especially for the
little Raspberry. Nginx is also very popular and less heavy on resources. But I
wanted something even simpler and had a look at lighttpd.  

Installing lighttpd is as easy as typing

    pacman -S lighttpd

All  configuration is done in the folder '/etc/lighttpd/'. There you find the
main configuration file 'lighttpd.conf':

    server.port             = 80
    server.username         = "http"
    server.groupname        = "http"
    server.document-root    = "/srv/http"
    server.errorlog         = "/var/log/lighttpd/error.log"
    dir-listing.activate    = "enable"
    index-file.names        = ( "index.html" )

Here you can set things like the port on which you want lighttpd to listen for
connections (port 80 is standard for the http protocol, i.e. "the internet" as
most people know it, so we don't need to change that).  The folder specified in
"server.document-root" is the place where lighttpd should look for the content
you want to deliver. The default folder "/srv/http" should already exist on
your system. If not, you can create it (or set the document root to any other
folder you want to serve content from). Just make sure that the user http
(lighttpd runs as a separate user for security reasons) can read this
directory. "server.errorlog" specifies the log file. If something is not working
as expected, this is a good place to look for clues. 

The option "dir-listing.activate" lets you control if you want anybody to be
able to get a listing of the directory content by typing something like
"mywebsite.org/subfolder" in the address bar of a browser. I recommend to
disable this option:
    
    dir-listing.activate    = "disable"

"index-file.names" controls the names of index files. A index file is something
like the entry point to your website. When someone navigates to your website,
this is the first thing he sees. From here you can build your website by linking
to other HTML files.

So, as a first test you can put a simple file "index.html" in your document
root ("/srv/http/", if you didn't change this):

    <!DOCTYPE html>
    <html>
        <body>
            <p>A Test!</p>
        </body>
    </html>

Now all we need to do is starting lighttpd:

    systemctl start lighttpd

If you want it to start automatically after every reboot:

    systemctl enable lighttpd

Now point a browser at the ip address of your Raspberry (or any other computer
you want to configure as server) and voila: you should see your first website!

[pi]: http://www.raspberrypi.org/
[light]:http://www.lighttpd.net/
[apa]:https://httpd.apache.org/
[ng]:http://nginx.org/
