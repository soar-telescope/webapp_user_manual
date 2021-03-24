.. role:: raw-html(raw)
    :format: html

Overview
########

We use Django and Django Rest Framework for build our backend API.

The `goodman-pipeline` package processes are very *granulated* as it should be.
But for a web application such as ours we found out that the best option was to
group many of the processes in blocks as described below. But in an observing
run there are many types of files. We have `calibration` and `science` files.

File Types
**********

Calibration files:
  Calibration files are ``BIAS`` and ``FLAT`` files. They need to be combined into
  *master BIAS* and *master FLATs*. Each proposal has also associated a dedicated
  *data reduction settings* and there can be defined, among other things, what
  are the minimum number of calibration files required to trigger a combination
  of a *master BIAS* or *FLAT*.

Science files:
  Science files are ``EXPOSE`` ``SPECTRUM`` and  ``ARC`` though one can argue
  that ``ARC`` are calibration files, in a general sense they are treated as
  science files in this case.



Process Blocks
**************

Reduce
  Identifies suitable master flats and master bias and applies the *basic* data
  reduction process. For spectroscopic data it also trims the non-illuminated
  areas which produce artifacts. In general the process looks like this:

  An ``EXPOSE`` files, which is the type given to *imaging data* can have the
  following process.

  **Image Trim** :raw-html:`&rarr;` **Bias Subtract**  :raw-html:`&rarr;` **Flatfielding** :raw-html:`&rarr;` **Cosmic Ray Removal**

  An ``SPECTRUM`` file will have the following:

  **Image Trim** :raw-html:`&rarr;`  **Slit Trim** :raw-html:`&rarr;` **Bias Subtract**  :raw-html:`&rarr;` **Flatfielding** :raw-html:`&rarr;` **Cosmic Ray Removal**

Extract
  Identifies targets in a ``SPECTRUM`` file and finds a suitable and compatible ``ARC`` lamps and performs fractional pixel
  extractions.

  **Identify** :raw-html:`&rarr;` **Trace** :raw-html:`&rarr;` **Extract**

Wavelength Calibration
  Using the extracted lamps it performs the wavelength calibration process
  using a template lamp from a library and series of cross correlations, then
  fits a mathematical model, resamples the spectrum to a linear dispersion axis
  and saves the file.


Flux Calibration
  This is not implemented yet but it will.

Astrometric Solution
  This functionality is under development.