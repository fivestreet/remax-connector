# Data sent to Integra

A rough structure of the json representation that should be expected by the integra api endpoint.

Fivestreet triggers a [POST] request to the provided url and expects a response with a 200 status code.
Please note that the structures bellow includes a ``meta`` key with additional information about the event.

## Agent

```
{
    "id": 50942,
    "meta": {
        "event_type": "create_account"
    },
    "name": "John Smith", 
    "email": "john.smith@example.com",
    "fivestreet_email": "name@fivestreet.me",
    "phone": "+1240000111",
    "confirmed_phone": false,
    "gmail_connected": true,
    "brokerage_agent_identifier": "1234",
    "brokerage_office_identifier": "5678",
    "twilio_phone": "+1240333222",
    "enabled": true,
    "rostered_members_count": 5,
    "claimed_at": "2013-11-01 20:35:49",
    "mls_identities": [
        {
            "board_name": "board 2",
            "board_id": "id 1"
        },
        { 
            "board_name": "board name 2",
            "board_id": "id 2"
        }
    ]
}
```

<table style="undefined;table-layout: fixed; width: 849px">
  <colgroup>
    <col style="width: 188px">
    <col style="width: 115px">
    <col style="width: 106px">
    <col style="width: 440px">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>integer</td>
    <td>unique identifier</td>
  </tr>
  <tr>
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible values: "create_account" or "update_account"</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>fivestreet_email</td>
    <td>string</td>
    <td>agent's fivestreet email</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>agent's phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>confirmed_phone</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>gmail_connected</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>brokerage_office_identifier</td>
    <td>string</td>
    <td>office account identifier provided by broker</td>
  </tr>
  <tr>
    <td>twilio_phone</td>
    <td>string</td>
    <td>agent's twilio assigned phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>enabled</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>rostered_members_count</td>
    <td>integer</td>
    <td>number of agents that are part of the agent/office roster</td>
  </tr>
  <tr>
    <td>claimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
</table>

## Lead

For extra data please refer to [remax-connector](https://github.com/fivestreet/remax-connector)

```
{
    "id": 20039,
    "meta": {
        "event_type": "create_lead"
    },
    "name": "James Andersen",
    "email": "james.andersen@example.com",
    "phone": "+12345678910",
    "source": "RE/MAX.com",
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
    "message": "I'm interested in this property",
    "owner": {
        "id": 1234,
        "name": "John Doe", 
        "email": "john.doe@example.com",
        "brokerage_agent_identifier": "21412",
        "brokerage_office_identifier": "341313"
    },
    "agent": {
        "id": 50942,
        "name": "John Smith", 
        "email": "john.smith@example.com",
        "brokerage_agent_identifier": "1234",
        "brokerage_office_identifier": "5678"
    },
    "claimed_at": "2013-11-01 20:35:49",
    "created_at": "2013-10-10 09:23:48",
    "extra_data": {}
}
```

<table style="undefined;table-layout: fixed; width: 849px">
  <colgroup>
    <col style="width: 188px">
    <col style="width: 115px">
    <col style="width: 106px">
    <col style="width: 440px">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>integer</td>
    <td>unique identifier</td>
  </tr>
  <tr>
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "create_lead"</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>email</td>
    <td>string</td>
    <td>prospect's email</td>
  </tr>
  <tr>
    <td>phone</td>
    <td>string</td>
    <td>agent's phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>source</td>
    <td>string</td>
    <td>the origin of the lead (Remax,Realtor and others)</td>
  </tr>
  <tr>
    <td>property.address.street</td>
    <td>string</td>
    <td>Street for the subject property</td>
  </tr>
  <tr>
    <td>property.address.city</td>
    <td>string</td>
    <td>City for the subject property</td>
  </tr>
  <tr>
    <td>property.address.state</td>
    <td>string</td>
    <td>State for the subject property</td>
  </tr>
  <tr>
    <td>property.address.zipcode</td>
    <td>string</td>
    <td>Zip code for the subject property</td>
  </tr>
  <tr>
    <td>property.address.country</td>
    <td>string</td>
    <td>Country for the subject property ("CA", "US")</td>
  </tr>
  <tr>
    <td>property.url</td>
    <td>string</td>
    <td>Url for the subject property</td>
  </tr>
  <tr>
    <td>property.price</td>
    <td>string</td>
    <td>price for the subject property</td>
  </tr>
  <tr>
    <td>property.mls_id</td>
    <td>string</td>
    <td>MLS ID for the subject property</td>
  </tr>
  <tr>
    <td>message</td>
    <td>string</td>
    <td>Inquiry message sent out by the prospect</td>
  <tr>
    <td>owner.id</td>
    <td>integer</td>
    <td>The fivestreet id of the owner agent</td>
  </tr>
  <tr>
    <td>owner.name</td>
    <td>integer</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>owner.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>owner.brokerage_agent_identifier</td>
    <td>string</td>
    <td>owner agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>owner.brokerage_office_identifier</td>
    <td>string</td>
    <td>owner office account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agent.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent that claimed the lead.</td>
  </tr>
  <tr>
    <td>agent.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>agent.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>referred_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
  <tr>
    <td>claimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
  <tr>
    <td>extra_data.(key)</td>
    <td>(key_type)</td>
    <td>Meta-data passed through</td>
  </tr>
</table>

## Referral

This event type takes place when a lead gets referred to a team or a group of agents.
The collection of agents represents all the agents that received the referral identified
by ``lead_id``.

_Note: this collection of agents can represent **n** agents_


```
{
    "lead_id": 20039,
    "meta": {
        "event_type": "refer_lead"
    },
    "referred_at": "2013-11-01 20:35:49",
    "agents": [
        {
            "id": 50942,
            "name": "John Smith", 
            "email": "john.smith@example.com",
            "brokerage_agent_identifier": "1234",
            "brokerage_office_identifier": "5678"
        },
        {
            "id": 233421,
            "name": "John Doe", 
            "email": "john.doe@example.com",
            "brokerage_agent_identifier": "1224",
            "brokerage_office_identifier": "5678"
        }
    ]
}
```

<table style="undefined;table-layout: fixed; width: 849px">
  <colgroup>
    <col style="width: 188px">
    <col style="width: 115px">
    <col style="width: 106px">
    <col style="width: 440px">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>lead_id</td>
    <td>integer</td>
    <td>The id of the lead</td>
  </tr>
  <tr>
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "refer_lead"</td>
  </tr>
  <tr>
    <td>referred_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
  <tr>
    <td>agents.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent</td>
  </tr>
  <tr>
    <td>agents.name</td>
    <td>integer</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>agents.email</td>
    <td>integer</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>agents.brokerage_agent_identifier</td>
    <td>integer</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agents.brokerage_office_identifier</td>
    <td>integer</td>
    <td>agent office identifier provided by broker</td>
  </tr>
</table>

## Claim

```
{
    "lead_id": 20039,
    "meta": {
        "event_type: "claim_lead"
    },
    "agent": {
        "id": 50942,
        "name": "John Smith", 
        "email": "john.smith@example.com",
        "brokerage_agent_identifier": "1234",
        "brokerage_office_identifier": "5678"
    },
    "claimed_at": "2013-11-01 20:35:49"
}
```

<table style="undefined;table-layout: fixed; width: 849px">
  <colgroup>
    <col style="width: 188px">
    <col style="width: 115px">
    <col style="width: 106px">
    <col style="width: 440px">
  </colgroup>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>lead_id</td>
    <td>integer</td>
    <td>The id of the lead</td>
  </tr>
  <tr>
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "claim_lead"</td>
  </tr>
  <tr>
    <td>agent.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent</td>
  </tr>
  <tr>
    <td>agent.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>agent.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>claimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
</table>
