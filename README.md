Created by Casper van Wezel (CW) on 2018-04-23:

Introduction
============
The DataManager is an application specifically made for OdinSpire.
The OdinSpire aims to IV test big batches of PV modules with a Spire Simulator and take EL images of all these modules as well.
All this data should then be combined into a nice report for the customer.

All this can be done with this application, since it grabs the flash data from the \*.ivc files on the Spire machine (ordered by last date), finds a matching EL using the serial number.
After this some manual information can be entered (for example the EL Inspection), after this the data is stored in a database and the LaTeX report is generated.

General
=======
For more information, have a look at the [Quick Manual for Developers](docs/manual_developers/manual_dev.pptx).

Cloud Database
--------------
For now the code does not contain the credentials for a cloud database account.
This should still be entered in:
`src/dbinterface/DatabaseInterface.java`


TODO
====

Marking EL images with cracks
-----------------------------
**Size:** L

Make a tool where the User can mark cracks by dragging 4 colored rectangles over the EL images.
The coordinates of these rectangles can then be stored in the database (and re-rendered when needed)

CRITICAL!


Export high-res EL images from database (as *.zip/*.tar or something)
---------------------------------------------------------------------
**Size:** M

Now the high-res images just go into the database, and there is no way to get them out.

nice-to-have, feature. But not needed now


Load high-res NEF file when desired (so when inspecting the images for example)
-------------------------------------------------------------------------------
**Size:** M

Now, the \*.NEF EL images are directly converted to a jpg of 1000px high, so the visual EL inspection is done on a low-res picture.
It is rather easy to also convert a high-res JPG and show that in the imageView.

feature, critical for High-Resolution image to judge the EL image

Display Status Saving + Compiling status is not shown untill the operations have been completed
-----------------------------
**Size:** M

This is a problem with the JavaFx GUI update thread or something

bug-fix, user experience

escape all LaTeX dangerous characters (# and \ for example )
-----------------------------
**Size:** S

Now there is no escaping done at all, so this might result in some future problems.

nice-to-have, improves fault tolerance

A bunch of small things:
------------------------

 * spire importer class: remove labels parameter (and use fields instead) (already partly done?!)
 * TableMeasurementIVEL: change hasEL true/false into 'yes'/'no' (and maybe set backgroundcolor red?)
 * Databaseviewer: make initial load of MeasurementInfo table just of last 100 results, and load all entries after button press
 * TestEngineer dropdown list + configuration file m
 * Add yearly callibration date as an input field (or at least link it to the machine serial, now hardcoded) (required before next calibration period)
 * databaseviewer: search option
 * Local database to improve responsiveness (and synchronize local->cloud)
