Reportek.Buildout
===================

Install - CDR
=============
::

    $ sudo bash
    $ apt-get install \
        python-dev libxslt1.1 libxslt-dev \
        lxml-dev libldap2-dev libsasl2-dev
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

    $ python boostrap.py -c prod.cfg
    $ bin/buildout -c buildout.cfg
    $ cp <usb-stick>/cdr/supervisord.conf .
    $ cp <usb-stick>/cdr/Data.fs /var/local/cdr/var/filestorage/Data.fs
    $ bin/supervisord

Install - CDR-CONVERTERS
========================
::

    $ cd /var/local
    $ mkdir /var/local/cdr-converters
    $ git clone https://github.com/eea/reportek-converters.git cdr-converters/deploy
    $ python ./cdr/virtualenv-1.10.1/virtualenv.py cdr-converters/sandbox
    $ cd cdr-converters
    $ chown -R zope:zope .
    $ su zope
    $ . sandbox/bin/activate
    $ pip install -r deploy/requirements.txt
    $ mkdir var
    $ cp <usb-stick>/cdr-converters/supervisord.conf
    $ sudo apt-get install unrar p7zip-full mdbtools wv xlhtml xsltproc unzip \
    $      ppthtml pdftohtml
    $ you need java to be installed
    $ install gdal>1.8 (see http://trac.osgeo.org/gdal/wiki/DownloadingGdalBinaries)
    $ mkdir deploy/lib
    $ wget -P /var/local/cdr-converters/deploy/lib http://archive.apache.org/dist/tika/tika-app-1.2.jar (current version is 1.4 but I didn't try it)
    $ nosetests
    $ supervisord

