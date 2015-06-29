FORMAT: 1A
HOST: https://domain.com

# RE/MAX and the FiveStreet Connector

The FiveStreet Connector will receive a lead from RE/Max, process the lead and send to FiveStreet. Once FiveStreet accepts the request, the FiveStreet Connector will return a 200 HTTP code to RE/Max. If there is an error during this process, an error message will be sent back to RE/Max. 

# Authentication

All requests must include a Authorization HTTP header, or a 401 (Unauthorized) response will be sent:

+ **Authorization: \<Base64 encoded value of "username:api_key"\>**

# HTTP Errors

Errors will be return using the following content-type. https://tools.ietf.org/html/draft-ietf-appsawg-http-problem-00

## Lead [/leads]

### Send data for a lead [POST]
+ Response 200 (application/json)

    + Body

            {
                "lead": {
                    "source": "RE/MAX.com",
                    "name": "John Smith",
                    "email": "john.smith@email.com",
                    "phone": "222-333-1234",
                    "message": "Belize, Belize",
                    "property": {
                      "address": "111 street address city ST zipcode",
                      "url": "http://property.com/url",
                      "list_price": "250000",
                      "mls_id": "88658565886"
                    },
                    "agent": {
                      "fivestreet_eamil": "agent@fivestreet.me",
                      "office": "Washington D.C."
                    },
                    "extra_data": {
                      "key": "value"
                    }
                }
            }

+ Response 401 (application/problem+json)

    + Headers

                WWW-Authenticate : Basic realm="Please specify a username and your API key for a password"

    + Body

            {
                "type": "https://domain.com/bad_api_key_error",
                "title": "Not Authorized",
                "detail": "Either no username/password was provided or it is not in our system."
            }
