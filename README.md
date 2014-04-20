Usage
----------

This image does not require any preconfiguration to run.  To use this image, map a directory from the host to `/var/lib/quasselcore`.

To run this image:

    /usr/bin/docker run -p 4242:4242 -v /path/to/quassel/storage:/var/lib/quasselcore --name=quassel-main hachque/quassel-core

What do these parameters do?

    -p 4242:4242 = forward the host's 4242 port to Quassel
    -v /path/to/quassel/storage:/var/lib/quasselcore = map the storage directory for Quassel
    --name quassel-main = the name of the container
    hachque/quassel-core = the name of the image

A systemd configuration file may look like:

    [Unit]
    Description=Quassel Main instance
    
    [Service]
    ExecStart=<command to start instance, see above>
    ExecStop=/usr/bin/docker stop quassel-main
    ExecStop=/usr/bin/docker rm quassel-main
    Restart=always
    RestartSec=5s
    
    [Install]
    WantedBy=multi-user.target

SSH / Login
--------------

**Username:** root

**Password:** linux

