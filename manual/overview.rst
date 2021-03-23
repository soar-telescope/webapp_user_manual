Overview
########

The Goodman Spectroscopic Pipeline Live is a web implementation of the
`Goodman Spectroscopic Pipeline <https://github.com/soar-telescope/goodman_pipeline>`_.
In summary the reduction process has been broken in several parts that might
include more than one step of the full process. Each of these parts has a
correspondent web API end point.

Reduce
  Identifies suitable master flats and master bias and applies the _basic_ data
  reduction process. For spectroscopic data it also trims the non-illuminated
  areas.

Extract
  Identifies targets and compatible ARC lamps and performs fractional pixel
  extractions.

Wavelength Calibration
  Using the extracted lamps it performs the wavelength calibration process.