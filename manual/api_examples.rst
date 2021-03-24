API Examples
############

.. warning::

   Always trust the API docs page instead because it is updated along the API itself.


Get the list of raw files
=========================

.. code-block:: python

   import requests

   api_key = 'some-fake-api-key-that-does-not-work'
   
   # define request headers
   headers = {'Authorization': f"Token {api_key}",
              'Content-Type': 'application/json'}

   #define parameters
   # 0: Raw files
   # 1: Calibration Files (Master flats or bias)
   # 2: Reduced files
   # 3: Extracted 1D spectrum
   # 4: Wavelength calibrated
   # 5: Flux Calibrated
   parameters = {"data_type": "0"}

   # remotehost should be replaced with the actual host
   # also the url can be composed as http://remotehost/api/files/?data_type=0
   # in that case you don't need to pass the params argument.
   response = requests.get(
            url='http://remotehost/api/files/',
            params=parameters,
            headers=headers)

   if response.status_code == 200:
       json_response = response.json()

   # alternatively you can use response.raise_for_status() and catch any exception

   from request.exceptions import HTTPError

   try:
       response.raise_for_status()
   except HTTPError as http_error:
       log.exception(http_error)




Will produce a response like this.  In this particular case the results have
been truncated to just a couple of results.

.. code-block:: json

    {
        "count": 545,
        "next": "http://remothost/gsp/api/files/?data_type=0&page=2",
        "previous": null,
        "results": [
            {
                "id": 952,
                "created": "2021-02-18T10:22:10.340053-03:00",
                "last_modified": "2021-02-18T10:22:13.470928-03:00",
                "original_file": "0001_GHTS_B_400m1_2x2_18-02-2021.fits",
                "original_file_id": 952,
                "parent_file": "0001_GHTS_B_400m1_2x2_18-02-2021.fits",
                "parent_file_id": 952,
                "file_name": "0001_GHTS_B_400m1_2x2_18-02-2021.fits",
                "directory_name": "/pipeline/data/20210218/RAW",
                "full_path": "/pipeline/data/20210218/RAW/0001_GHTS_B_400m1_2x2_18-02-2021.fits",
                "obstype": "LAMPFLAT",
                "object": "DFLAT",
                "filter": "NO_FILTER",
                "filter_2": "NO_FILTER",
                "grating": "400_SYZY",
                "slit": "1.0_LONG_SLIT",
                "cam_targ": "11.6",
                "grt_targ": "5.8",
                "obsra": "17:38:33.320",
                "obsdec": "-48:23:59.899",
                "gain": "1.4",
                "rdnoise": "4.74",
                "roi": "Spectroscopic 2x2",
                "wavmode": "400_M1",
                "proposal_id": "calibrate",
                "observation_id": null,
                "configuration_id": null,
                "block_id": null,
                "image_id": 1,
                "date": "2021-02-18",
                "data_type": "0",
                "normalized": false,
                "technique": "Spectroscopy",
                "saturation_value": 49928
            },
            {
                "id": 900,
                "created": "2020-11-26T21:30:52.692308-03:00",
                "last_modified": "2020-11-26T21:30:55.204647-03:00",
                "original_file": "0354_Orion-Burst_26-11-2020_comp.fits",
                "original_file_id": 900,
                "parent_file": "0354_Orion-Burst_26-11-2020_comp.fits",
                "parent_file_id": 900,
                "file_name": "0354_Orion-Burst_26-11-2020_comp.fits",
                "directory_name": "/pipeline/data/20201126/RAW",
                "full_path": "/pipeline/data/20201126/RAW/0354_Orion-Burst_26-11-2020_comp.fits",
                "obstype": "ARC",
                "object": "ZTF20actqfpc",
                "filter": "NO_FILTER",
                "filter_2": "GG455",
                "grating": "400_SYZY",
                "slit": "1.0_LONG_SLIT",
                "cam_targ": "16.1",
                "grt_targ": "7.5",
                "obsra": "05:34:22.372",
                "obsdec": "-5:24:52.448",
                "gain": "1.48",
                "rdnoise": "3.89",
                "roi": "Spectroscopic 2x2",
                "wavmode": "400_M2",
                "proposal_id": "SOAR2020B-008",
                "observation_id": 1,
                "configuration_id": 1,
                "block_id": 0,
                "image_id": 34304,
                "date": "2020-11-26",
                "data_type": "0",
                "normalized": false,
                "technique": "Spectroscopy",
                "saturation_value": 69257
            },
            {
                "id": 895,
                "created": "2020-11-26T19:37:53.519510-03:00",
                "last_modified": "2020-11-26T19:37:55.892156-03:00",
                "original_file": "0353_Orion-Burst_26-11-2020_comp.fits",
                "original_file_id": 895,
                "parent_file": "0353_Orion-Burst_26-11-2020_comp.fits",
                "parent_file_id": 895,
                "file_name": "0353_Orion-Burst_26-11-2020_comp.fits",
                "directory_name": "/pipeline/data/20201126/RAW",
                "full_path": "/pipeline/data/20201126/RAW/0353_Orion-Burst_26-11-2020_comp.fits",
                "obstype": "ARC",
                "object": "ZTF20actqfpc",
                "filter": "NO_FILTER",
                "filter_2": "GG455",
                "grating": "400_SYZY",
                "slit": "1.0_LONG_SLIT",
                "cam_targ": "16.1",
                "grt_targ": "7.5",
                "obsra": "05:34:22.372",
                "obsdec": "-5:24:52.448",
                "gain": "1.48",
                "rdnoise": "3.89",
                "roi": "Spectroscopic 2x2",
                "wavmode": "400_M2",
                "proposal_id": "SOAR2020B-008",
                "observation_id": 1,
                "configuration_id": 1,
                "block_id": 0,
                "image_id": 34304,
                "date": "2020-11-26",
                "data_type": "0",
                "normalized": false,
                "technique": "Spectroscopy",
                "saturation_value": 69257
            }
        ]
    }


Add Collaborator to Proposal
============================


.. code-block:: python

   import requests

   api_key = 'some-fake-api-key-that-does-not-work'

   # define request headers
   headers = {'Authorization': f"Token {api_key}",
              'Content-Type': 'application/json'}

   #define payload
   payload = {
       "email": "user@server.net",
       "action": "add"
       }


   # remotehost should be replaced with the actual host
   response = requests.get(
            url='http://remotehost/api/proposals/collaborators/5/',
            data=payload,
            headers=headers)

   if response.status_code == 200:
       json_response = response.json()



You get a serialized version of the proposal database instance.

.. code-block:: json

    {
        "id": 5,
        "soar_id": "calibrate",
        "semester": "2020A",
        "title": "Calibrations",
        "abstract": "How calibrations will be handled.",
        "user": {
            "id": 3,
            "username": "observer",
            "last_login": "2020-10-24T18:56:45.976000-03:00",
            "first_name": "Observer",
            "last_name": "Observer",
            "email": "observer@observatory.cl",
            "is_staff": true,
            "is_active": true,
            "date_joined": "2019-11-13T10:26:23-03:00"
        },
        "collaborators": [
            {
                "id": 41,
                "username": "user",
                "last_login": null,
                "first_name": "",
                "last_name": "",
                "email": "user@server.net",
                "is_staff": false,
                "is_active": true,
                "date_joined": "2021-03-24T15:32:23.329399-03:00"
            }
        ]
    }

Since the user did not exists a new user was created.