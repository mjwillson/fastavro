
Welcome to fastavro's documentation!
====================================


Contents:

.. toctree::
   :maxdepth: 2


The current Python `avro` package is packed with features but dog slow.

On a test case of about 10K records, it takes about 14sec to iterate over all of
them. In comparison the JAVA `avro` SDK does it in about 1.9sec.

`fastavro` is less feature complete than `avro`, however it's much faster. It
iterates over the same 10K records in 2.9sec, and if you use it with PyPy it'll
do it in 1.5sec (to be fair, the JAVA benchmark is doing some extra JSON
encoding/decoding).

If the optional C extension (generated by `Cython`_) is available, then
`fastavro` will be even faster. For the same 10K records it'll run in about
1.7sec.

.. _`Cython`: http://cython.org/

You can also use the `fastavro` script from the command line to dump `avro`
files. Each record will be dumped to standard output in one line of JSON.
::

    fastavro weather.avro

You can also dump the avro schema::

    fastavro --schema weather.avro

fastavro script
---------------
::

    usage: fastavro [-h] [--schema] [--version] file [file ...]

    iter over avro file, emit records as JSON

    positional arguments:
      file        file(s) to parse

    optional arguments:
      -h, --help  show this help message and exit
      --schema    dump schema instead of records
      --version   show program's version number and exit


fastavro module
---------------
.. automodule:: fastavro
   :members:


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

