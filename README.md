FORMAT: 1A
HOST: https://domain.com

# RE/MAX and the FiveStreet Connector

The FiveStreet Connector will receive a lead from RE/MAX, process the lead and send to FiveStreet. Once FiveStreet accepts the request, the FiveStreet Connector will return a 200 HTTP code to RE/MAX. If there is an error during this process, an error message will be sent back to RE/MAX. 

# Authentication

All requests must include a Authorization HTTP header, or a 401 (Unauthorized) response will be sent:

+ **Authorization: \<Base64 encoded value of "username:api_key"\>**

# HTTP Errors

Errors will be returned as a http problem. (https://tools.ietf.org/html/draft-ietf-appsawg-http-problem-00)

## Lead [/leads]

### Send data for a lead [POST]
+ Response 200 (application/json)

    + Body

            {
                "lead": {
                    "source": "RE/MAX.com",
                    "sub_source": "Listing Inquiry",
                    "name": "John Smith",
                    "email": "john.smith@email.com",
                    "phone": "222-333-1234",
                    "message": "I'm Interested in viewing this property",
                    "property": {
                        "address": {
                            "street":"111 street address",
                            "city" : "Seattle",
                            "state" : "WA",
                            "zipcode" : "98230",
                            "country" : "US"
                        },
                        "url": "http://property.com/url",
                        "list_price": "250000",
                        "mls_id": "88658565886"
                    },
                    "extra_data": {
                        "is_rental" : "true",
                        "web_activity_url": "http://webactivity.url/",
                        "key": "value"
                    }
                },
                "routing_rules": 
                    [   {
                            "agent_id" : "12345",
                            "type" : "favorited",
                            "office_id": "A987678"
                        },
                        {
                            "agent_id" : "67890",
                            "type" : "listing_agent",
                            "office_id": "A15784"
                        }
                    ]
            }
    
    + All values are strings
    + Routing Rules Type can be of type "direct_to_agent", "connected", "favourited", "listing_agent", "new_lead"
    + <table style="undefined;table-layout: fixed; width: 849px">
        <colgroup>
        <col style="width: 188px">
        <col style="width: 115px">
        <col style="width: 106px">
        <col style="width: 440px">
        </colgroup>
          <tr>
            <th>Name</th>
            <th>Format</th>
            <th>Required</th>
            <th>Description</th>
          </tr>
          <tr>
            <td>source</td>
            <td>string</td>
            <td>Yes</td>
            <td>The main source of the lead e.g. "Remax.com"</td>
          </tr>
          <tr>
            <td>sub_source</td>
            <td>string</td>
            <td>No</td>
            <td>The sub source of the lead e.g "Listing Inquiry"</td>
          </tr>
          <tr>
            <td>name</td>
            <td>string</td>
            <td>No</td>
            <td>The name of the lead</td>
          </tr>
          <tr>
            <td>email</td>
            <td>string</td>
            <td>Yes if phone not provided</td>
            <td>The email of the lead</td>
          </tr>
          <tr>
            <td>phone</td>
            <td>string</td>
            <td>Yes if email not provided</td>
            <td>The phone number of the lead</td>
          </tr>
          <tr>
            <td>message</td>
            <td>string</td>
            <td>No</td>
            <td>Any additional messages submitted with the lead</td>
          </tr>
          <tr>
            <td>property.address.street</td>
            <td>string</td>
            <td>No</td>
            <td>Street Address for the subject property</td>
          </tr>
          <tr>
            <td>property.address.city</td>
            <td>string</td>
            <td>No</td>
            <td>City for the subject property</td>
          </tr>
          <tr>
            <td>property.address.state</td>
            <td>string</td>
            <td>No</td>
            <td>State for the subject property</td>
          </tr>
          <tr>
            <td>property.address.zipcode</td>
            <td>string</td>
            <td>Yes</td>
            <td>Zip code for the subject property</td>
          </tr>
          <tr>
            <td>property.address.country</td>
            <td>"US", "CA"</td>
            <td>No</td>
            <td>Country for the subject property</td>
          </tr>
          <tr>
            <td>property.url</td>
            <td>string</td>
            <td>No</td>
            <td>Url for the subject property</td>
          </tr>
          <tr>
            <td>property.list_price</td>
            <td>string</td>
            <td>No</td>
            <td>List price for the subject property</td>
          </tr>
          <tr>
            <td>property.mls_id</td>
            <td>string</td>
            <td>No</td>
            <td>MLS ID for the subject property</td>
          </tr>
          <tr>
            <td>extra_data</td>
            <td>&lt;string,string&gt;</td>
            <td>Yes</td>
            <td>Extra data like search history url</td>
          </tr>
          <tr>
            <td>routing_rules.agent_id</td>
            <td>string</td>
            <td>Yes</td>
            <td>The RE/MAX ID for the agent</td>
          </tr>
          <tr>
            <td>routing_rules.type</td>
            <td>"direct_to_agent",<br>"favorited",<br/>"connected",<br/>"listing_agent",<br/>"new_lead"</td>
            <td>Yes if agent_id provide</td>
            <td>The type of routing logic to employ</td>
          </tr>
          <tr>
            <td>routing_rules.office_id</td>
            <td>string</td>
            <td>Yes if agent_id not provided</td>
            <td>The office ID for the agent</td>
          </tr>
        </table>

+ Response 401 (application/problem+json)

    + Headers

                WWW-Authenticate : Basic realm="Please specify a username and your API key for a password"

    + Body

            {
                "type": "https://domain.com/bad_api_key_error",
                "title": "Not Authorized",
                "detail": "Either no username/password was provided or it is not in our system."
            }
