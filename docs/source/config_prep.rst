===========                                      
config_prep
===========
| The "config_prep" file defines parameters used during data preparation, when reading data. This file contains parameters used by script written for APS 34-IDC beamline.

Parameters
==========

- data_dir:
| mandatory for the 34-IDC prep, the directory containing raw data. This directory will have several subdirectories each containing tif format data files. Each subdirectory represents separate scan and is numbered with the scan index
| example:
::

    data_dir = "/path/to/data/files/ADStaff19-1a"                                             

- darkfield_filename:
| optional, depending on the detector. Dark field file taken to clean bad pixels or correct background in CCD. Each detector needs to implement this correctly.
| example:
::

    darkfield_filename = "/path/to/darkfield_file/dark.tif"

- whitefield_filename:
| optional, depending on the detector. White field file taken to correct over saturated pixels. Each detector needs to implement this correctly.
| example:
::

    whitefield_filename = "/path/to/whitefield_file/whitefield.tif"

- roi:
| typically read from a spec file, but if not present there, must be configured. Defines the region of a detector that the data has been read from. Needed to determine corrections on the detector. The values in the list (refer to example below) are as follows: x coordinate starting point, x length, y coordinate starting point, y length.
| example:
::

    roi = [0,256,0,256]

- min_files:
| optional, defines a minimum number of raw data files in the scan directory. If number of files is less than minimum, the directory is not added to the data. 
| example:
::

     min_files = 80

- exclude_scans:
| a list containing scan indexes that will be excluded from preparation
| example:
::

    exclude_scans = [78,81]

- separate_scans:
| in typical scenario the data from all scans in experiment are combined. If specified as separate scans, each scan will be processed separately and will have sub-experiment name containing scan index ex. "scan_9", where 9 is scan index
| example:
::

   separate_scans = False

- separate_scan_ranges:
| in typical scenario the data from all scans in experiment are combined. If specified as separate scan ranges, each scan or scan range in the experiment will be processed separately and will have sub-experiment name containing scan index ex. "scan_9", where 9 is scan index, or "scan_10-15", where 10-15 is the scan range. The scans and scan ranges are defined in main configuration "config" file as scan parameter, and are part of experiment name.
| example:
::

   separate_scan_ranges = True

- Imult:
| Optional, defaults to the average of the whitefield. A multiplication factor used to renormalize the whitefield correction.
| example:
::

   Imult = 1000000

- detector:                  
| optional, can be omitted if roi param is specified
| example:
::

    detector = "34idcTIM2"

