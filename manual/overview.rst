Overview
########

We use Django and Django Rest Framework for build our backend API.


The `goodman-pipeline` package processes are very _granulated_ as it should be.
But for a web application such ours we found out that the best option was to b


Reduce
  Identifies suitable master flats and master bias and applies the _basic_ data
  reduction process. For spectroscopic data it also trims the non-illuminated
  areas which produce artifacts.

Extract
  Identifies targets and compatible ARC lamps and performs fractional pixel
  extractions.

Wavelength Calibration
  Using the extracted lamps it performs the wavelength calibration process.

Flux Calibration
  This is not implemented yet but it will.

Astrometric Solution
  This functionality is under development.