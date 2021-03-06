.. _saltlog:

*******
saltlog
*******


Name
====

saltlog -- Create FITS table of observations from image headers

Usage
=====

saltlog images outfile (clobber) logfile (verbose) status

Parameters
==========


*images*
    String. List of input images including, if necessary, absolute or
    relative paths to the data. Data can be provided as a comma-separated
    list, or a string with a wildcard (e.g. 'images=S20061210*.fits'), or
    a foreign file containing an ascii list of image filenames. For ascii
    list option, the filename containing the list must be provided
    preceded by a '@' character, e.g. 'images=@listoffiles.lis'. saltlog
    currently searches for the PROPID and PROPOSER keywords which are
    not native to raw images. They are written by the tool saltedtky which
    should be run prior to saltlog to get full value from the observation
    log.

*outfile*
    String. The name of a FITS table file containing output from
    saltlog. If the output is intended for a different directory the
    absolute or relative path must be supplied with the file name.

*(clobber)*
    Hidden boolean. If set to 'yes' an existing file of the same name will
    be overwritten by outfile.

*logfile*
    String. Name of an ascii file for storing log and error messages
    written by the task. The file may be new, or messages can also be
    appended to a pre-existing file.

*(verbose)*
    Boolean. If verbose=n, log messages will be suppressed.

*(status)*
    Integer. Provided status=0 is passed to saltlog, a successful run of
    the task will yield status=0 at completion of the task.  Any other
    value for the status flag at completion indicates failed execution.

Description
===========


saltlog collates all primary keyword headers from a list of input
files and creates a tabuated observing log in FITS format. The table
contains one column for each keyword and one row for each exposure in
a sequence. The first column of the table contains the file name.

The advantage of creating an observation table is convenience but it's
use is possibly limited to the period of time before the SALT database
comes online. File contents can be understood, examined and filtered
without going to the expense of opening the large image files
themselves. most useful during pipeline processing.

Examples
========

1. To create a FITS observation log from a list of image files::

    --> saltlog images='@images.lis' outfile='obslog.fits'
    clobber='no' logfile='salt.log' verbose='yes'

Time and disk requirements
==========================

Individual unbinned full frame RSS image files can be 112MB in
size. It is recommended to use workstations with a minimum of 512MB
RAM. On a contemporary linux machine, one hundred files can be
processed in ~ 1 sec.

Bugs and limitations
====================

Send feedback and bug reports to salthelp@saao.ac.za

See also
========

 :ref:`saltpipe` :ref:`saltclean`