.. _v1/keys-list:

Profiles API v1: List API keys
==============================
``GET`` ``https://api.mollie.com/v1/profiles/*id*/apikeys``

Authentication: :ref:`OAuth access tokens <oauth/overview>`

List the active API keys for the given payment profile.

**Note that you cannot retrieve API keys for a different account than your own, even if you have a valid OAuth token.**

If you wish to create a payment on behalf of a different merchant, use your app's access token and the ``profileId`` of
one of the merchant's payment profiles when :ref:`creating a payment <v1/payments-create>`.

Parameters
----------
Replace ``id`` in the endpoint URL by the payment profile's ID, for example ``pfl_v9hTwCvYqw``.

Response
--------
``200`` ``application/json; charset=utf-8``

.. list-table::
   :widths: auto

   * - | ``count``
       | integer
     - The number of API keys found in ``data``.

   * - | ``data``
       | array
     - An array of API key objects as described in :ref:`Get API key <v1/keys-get>`.

Example
-------

Request
^^^^^^^
.. code-block:: bash

   curl -X GET https://api.mollie.com/v1/profiles \
       -H "Authorization: Bearer access_Wwvu7egPcJLLJ9Kb7J632x8wJ2zMeJ"

Response
^^^^^^^^
.. code-block:: http

   HTTP/1.1 200 OK
   Content-Type: application/json; charset=utf-8

   {
       "count": 2,
       "data": [
           {
               "resource": "profile_api_key",
               "id": "live",
               "key": "live_eSf9fQRwpsdfPY8y3tUFFmqjADRKyA",
               "createdDatetime": "2018-03-17T01:47:47.0Z"
           },
           {
               "resource": "profile_api_key",
               "id": "test",
               "key": "test_UgfUyzqgrbh6dAfjYBQTMhPD3nQTda",
               "createdDatetime": "2018-03-17T01:47:47.0Z"
           }
       ]
   }