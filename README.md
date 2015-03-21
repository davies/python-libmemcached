python-libmemcached is a python wrapper for libmemcached.

=== Features ===
support libmemcached-1.
support large item (>=1M), auto splitting and merging
configable item compression and decompression when needed
use marshal prior to cPickle when serializing.
nonblock by default
fail-over patch for libmemcached-0.40
empty string patch for libmemcached-0.40
set_multi, prepend_multi, delete_multi
buffer requests patch for libmemcached-0.40
Dependence
libmemcached 0.40
python 2.5+
Pyrex 0.9.4+
Install
1. Download libmemcached 0.40 and python-libmemcached 0.40, and extract them.

$ wget http://launchpad.net/libmemcached/1.0/0.40/+download/libmemcached-0.40.tar.gz
$ tar zxf libmemcached-0.40.tar.gz
$ wget http://python-libmemcached.googlecode.com/files/python-libmemcached-0.40.tar.gz
$ tar zxf python-libmemcached-0.40.tar.gz
2. patch libmemcached, and install it

cd libmemcached-0.40
patch -p1 < ../ython-libmemcached/patches/empty_string.patch
patch -p1 < ../ython-libmemcached/patches/request_buffer.patch
patch -p1 < ../ython-libmemcached/patches/fail_over.patch
./configure
make
make install
3. install python-libmemcached 0.40

cd  python-libmemcached ; 
python setup.py build
sudo python setup.py install
4.Test

python benchmark.py

1.It needs libmemcached >=1.0.2 (touch support), patched with behavior.patch, empty_string.patch, touch_expire.patch
2.If you use the python whose version is < 2.5, you should modify the Py_ssize_t definition.
