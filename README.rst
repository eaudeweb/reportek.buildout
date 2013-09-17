===================
Reportek.Buildout
===================

Install
=======
::
    $ sudo bash
    $ mkdir /var/local/cdr
    $ cp <usb-stick>/repository/* /var/local/cdr
    $ adduser zope
    $ cd cdr
    $ chown -R zope:zope .
    $ su zope
    $ tar xvfz virtualenv-1.10.1.tar.gz
    $ ./virtualenv-1.10.1/virtualenv.py sandbox
    $ . bin/sandbox/activate
    $ rm -rf virtualenv-1.10.1

    $ python boostrap.py -d -c prod.cfg
    $ bin/buildout -c buildout.cfg
