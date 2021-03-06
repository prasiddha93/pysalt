.. _specsky:

*******
specsky
*******


Name
====

specsky-- Sky Subtract 2-D spectroscopic data

Usage
=====

specsky images outimages outpref (method) (section) (thresh)
(clobber) (logfile) (verbose)

Parameters
==========


*images*
    String. List of FITS images to prepare. Data can be provided as a
    comma-separated list, or a string with a wildcard
    (e.g. 'images=S20061210*.fits'), or a foreign file containing an ascii
    list of image filenames. For the ascii list option, the filename
    containing the list must be provided preceded by a '@' character,
    e.g. 'images=@listoffiles.lis'. The list can contain data files from
    multiple SALT instruments.

*outimage*
    String. A list of images. Data can be provided as a comma-separated
    list, or a string with a wildcard (e.g. 'outimages=rS20061210*.fits'), or
    a foreign file containing an ascii list of image filenames. For ascii
    list option, the filename containing the list must be provided
    preceded by a '@' character, e.g. 'outimages=@listoffiles.lis'. This list
    must be of the same size as the images argument list.

*outpref*
    String. If the outpref string is non-zero in length and contains
    characters other than a blank space, it will override any value of the
    outimages argument. Output file names will use the name list provided
    in the images argument, but adding a prefix to each output file
    defined by outpref. An absolute or relative directory path can be
    included in the prefix, e.g. 'outpref=/Volumes/data/p'.

*(method)*
    String.  The method to use for sky subtraction.  Currently, the only
    option is 'normal' where lines will be extracted from the region
    specified by section to be subtracted.

*(clobber)*
    Hidden boolean. If set to 'yes' files contained within the outpath
    directory will be overwritten by newly created files of the same
    name.

*(logfile)*
    String. Name of an ascii file for storing log and error messages
    from the tool. The file may be new, or messages can also be appended to a
    pre-existing file.

*(verbose)*
    Hidden Boolean. If verbose=n, log messages will be suppressed.

Description
===========


SPECSKY will subtract sky regions from the data.   The task currently only
has one mode of operations which is 'normal'.  In this mode, the task
estimates the skylines from a region in the image specified by section.  These
skylines will then be subtracted from the rest of the image.

EXAMPLES
1. To subtract sky lines with specsky::

    --> specsky images='pmbxpP*.fits' outimages= outpref='r'
    method='normal' section='[1200:1500]' logfile='salt.log'

Time and disk requirements
==========================

Individual unbinned raw full-frame RSS files can be 112MB in size. It is
recommended to use workstations with a minimum of 512MB RAM. On a
linux machine with 2.8 Ghz processor and 2 Gb of RAM, one 2051x2051 image
in 0.15 sec.

Bugs and limitations
====================

The sky subtraction algorithm needs to be improved as it is very simple
and does not account for a number of effects.

Send feedback and bug reports to salthelp@saao.ac.za

See also
========

 :ref:`specidentify`