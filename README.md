FORMAT: 1A
HOST: https://domain.com

# RE/MAX Connector

Add description here

# Authentication

All requests must include a Authorization HTTP header, or a 401 (Unauthorized) response will be sent:

+ **Authorization: \<Base64 encoded value of "username:api_key"\>**

# HTTP Errors

https://tools.ietf.org/html/draft-ietf-appsawg-http-problem-00

## Lead [/leads]

### Send data for a lead [POST]
+ Response 202 (application/json)

    + Body

            {
                "lead": {
                    "source": "RE/MAX.com",
                    "listing_id": "69866769696768",
                    "name": "John Smith",
                    "email": "john.smith@email.com",
                    "phone": "222-333-1234",
                    "message": "Belize, Belize",
                    "property": {
                      "address": "111 street address city ST zipcode",
                      "url": "http://property.com/url",
                      "list_price": "250000"
                    },
                    "agent": {
                      "fivestreet_eamil": "agent@fivestreet.me",
                      "office": "Washington D.C."
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

+ Questions/Notes:

  1. One at a time or batch process?
  2. How are we planning on handling if fivestreet is down?
  3. What if another system is down?
  4. Is it fair to say, all leads come from a listing?
  5. Remove Other custome fields, since they are not defined.
