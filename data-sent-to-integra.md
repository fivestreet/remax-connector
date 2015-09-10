# FiveStreet hooks

A rough structure of the json representation that should be expected by the integra api endpoint.

Fivestreet triggers a [POST] request to the provided url and expects a response with a 200 status code.
Please note that the structures bellow includes a ``meta`` key with additional information about the event.

## Agent

```
{
    "meta": {
        "event_type": "create_agent"
    },
    agent: {
        "id": 50942,
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible values: "create_agent" or "update_agent"</td>
  </tr>
  <tr>
    <td>agent.id</td>
    <td>integer</td>
    <td>unique identifier</td>
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
    <td>agent.fivestreet_email</td>
    <td>string</td>
    <td>agent's fivestreet email</td>
  </tr>
  <tr>
    <td>agent.phone</td>
    <td>string</td>
    <td>agent's phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>agent.confirmed_phone</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>agent.gmail_connected</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>office account identifier provided by broker</td>
  </tr>
  <tr>
    <td>agent.twilio_phone</td>
    <td>string</td>
    <td>agent's twilio assigned phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>agent.enabled</td>
    <td>boolean</td>
    <td>true/false</td>
  </tr>
  <tr>
    <td>agent.rostered_members_count</td>
    <td>integer</td>
    <td>number of agents that are part of the agent/office roster</td>
  </tr>
</table>

## Lead

For extra data please refer to [remax-connector](https://github.com/fivestreet/remax-connector)

```
{
    "meta": {
        "event_type": "create_lead"
    },
    "lead": {
        "id": 20039,
        "name": "James Andersen",
        "email": "james.andersen@example.com",
        "phone": "+12345678910",
        "source": "RE/MAX.com",
        "property": {
            "address": {
                "street":"111 street address",
                "city" : "Seattle",
                "state" : "WA",
                "zipcode" : "98230"
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
        "claimed_at": "2012-04-23T18:25:43.511Z",
        "created_at": "2013-10-10T09:23:48.552Z",
        "extra_data": {}
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "create_lead"</td>
  </tr>
  <tr>
    <td>lead.id</td>
    <td>integer</td>
    <td>unique identifier</td>
  </tr>
  <tr>
    <td>lead.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>lead.email</td>
    <td>string</td>
    <td>prospect's email</td>
  </tr>
  <tr>
    <td>lead.phone</td>
    <td>string</td>
    <td>agent's phone number with the country prefix included.</td>
  </tr>
  <tr>
    <td>lead.source</td>
    <td>string</td>
    <td>the origin of the lead (Remax,Realtor and others)</td>
  </tr>
  <tr>
    <td>lead.property.address.street</td>
    <td>string</td>
    <td>Street for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.address.city</td>
    <td>string</td>
    <td>City for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.address.state</td>
    <td>string</td>
    <td>State for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.address.zipcode</td>
    <td>string</td>
    <td>Zip code for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.url</td>
    <td>string</td>
    <td>Url for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.price</td>
    <td>string</td>
    <td>price for the subject property</td>
  </tr>
  <tr>
    <td>lead.property.mls_id</td>
    <td>string</td>
    <td>MLS ID for the subject property</td>
  </tr>
  <tr>
    <td>lead.message</td>
    <td>string</td>
    <td>Inquiry message sent out by the prospect</td>
  <tr>
    <td>lead.owner.id</td>
    <td>integer</td>
    <td>The fivestreet id of the owner agent</td>
  </tr>
  <tr>
    <td>lead.owner.name</td>
    <td>integer</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>lead.owner.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>lead.owner.brokerage_agent_identifier</td>
    <td>string</td>
    <td>owner agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>lead.owner.brokerage_office_identifier</td>
    <td>string</td>
    <td>owner office account identifier provided by broker</td>
  </tr>
  <tr>
    <td>lead.agent.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent that claimed the lead.</td>
  </tr>
  <tr>
    <td>lead.agent.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>lead.agent.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>lead.agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>lead.agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>lead.referred_at</td>
    <td>string</td>
    <td>Date represented as a string; format: YYYY-MM-DDTHH:MM:SS.:::Z</td>
  </tr>
  <tr>
    <td>lead.claimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: YYYY-MM-DDTHH:MM:SS.:::Z</td>
  </tr>
  <tr>
    <td>lead.extra_data.(key)</td>
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
    "meta": {
        "event_type": "refer_lead"
    },
    "referral": {
        "lead_id": 20039,
        "referred_at": "2013-10-10T09:23:48.552Z",
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "refer_lead"</td>
  </tr>
  <tr>
    <td>referral.lead_id</td>
    <td>integer</td>
    <td>The id of the lead</td>
  </tr>
  <tr>
    <td>referral.referred_at</td>
    <td>string</td>
    <td>Date represented as a string; format: YYYY-MM-DDTHH:MM:SS.:::Z</td>
  </tr>
  <tr>
    <td>referral.agents.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent</td>
  </tr>
  <tr>
    <td>referral.agents.name</td>
    <td>integer</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>referral.agents.email</td>
    <td>integer</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>referral.agents.brokerage_agent_identifier</td>
    <td>integer</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>referral.agents.brokerage_office_identifier</td>
    <td>integer</td>
    <td>agent office identifier provided by broker</td>
  </tr>
</table>

## Claim

```
{
    "meta": {
        "event_type: "claim_lead"
    },
    "claim": {
      "lead_id": 20039,
      "agent": {
          "id": 50942,
          "name": "John Smith", 
          "email": "john.smith@example.com",
          "brokerage_agent_identifier": "1234",
          "brokerage_office_identifier": "5678"
      },
      "claimed_at": "2013-10-10T09:23:48.552Z"
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "claim_lead"</td>
  </tr>
  <tr>
    <td>claim.lead_id</td>
    <td>integer</td>
    <td>The id of the lead</td>
  </tr>
  <tr>
    <td>claim.agent.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent</td>
  </tr>
  <tr>
    <td>claim.agent.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>claim.agent.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>claim.agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>claim.agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>claim.claimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: YYYY-MM-DDTHH:MM:SS.:::Z</td>
  </tr>
</table>

## Unclaim

```
{
    "meta": {
        "event_type: "unclaim_lead"
    },
    "unclaim": {
      "lead_id": 20039,
      "agent": {
          "id": 50942,
          "name": "John Smith", 
          "email": "john.smith@example.com",
          "brokerage_agent_identifier": "1234",
          "brokerage_office_identifier": "5678"
      },
      "unclaimed_at": "2013-10-10T09:23:48.552Z"
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "unclaim_lead"</td>
  </tr>
  <tr>
    <td>unclaim.lead_id</td>
    <td>integer</td>
    <td>The id of the lead</td>
  </tr>
  <tr>
    <td>unclaim.agent.id</td>
    <td>integer</td>
    <td>The fivestreet id of the agent</td>
  </tr>
  <tr>
    <td>unclaim.agent.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>unclaim.agent.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>unclaim.agent.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>unclaim.agent.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>unclaim.unclaimed_at</td>
    <td>string</td>
    <td>Date represented as a string; format: YYYY-MM-DDTHH:MM:SS.:::Z</td>
  </tr>
</table>

# Connector hooks

## Assign Lead

This event will indicate when a lead has been assigned an office or routed to an agent based on connected agent logic inside the FiveStreet Connector.

```
{
    "meta": {
        "event_type: "assign_lead"
    },
    “assign": {
      “lead": {
        "name": "James Andersen",
        "email": "james.andersen@example.com",
        "phone": "+12345678910",
        "zipcode": "90210",
        "source": "RE/MAX.com",
        "sub_source": "Listing Inquiry",
        "brokerage_agent_identifier": "1234",
        "brokerage_agent_type": "favourited",
        "brokerage_office_identifier": "5678"
      },
      “assigned_at": "2013-11-01 20:35:49"
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "assign_lead"</td>
  </tr>
  <tr>
    <td>assign.lead.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>assign.lead.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>assign.lead.zipcode</td>
    <td>string</td>
    <td>Zip code for the inquiry</td>
  </tr>
  <tr>
    <td>assign.lead.source</td>
    <td>string</td>
    <td>the origin of the lead (Remax,Realtor and others)</td>
  </tr>
  <tr>
    <td>assign.lead.sub_source</td>
    <td>string</td>
    <td>the secondary origin of the lead (Listing Inquiry, Agent Profile etc)</td>
  </tr>
  <tr>
    <td>assign.lead.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>assign.lead.brokerage_agent_type</td>
    <td>string</td>
    <td>type of routing for the agent e.g. "favourited","connected" etc</td>
  </tr>
  <tr>
    <td>assign.lead.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>assign.assigned_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
</table>

## Reassign Lead

This event will indicate the connector is reprocessing the lead due to error received from FiveStreet.

```
{
    "meta": {
        "event_type: "reassign_lead"
    },
    “reassign": {
      “lead": {
        "name": "James Andersen",
        "email": "james.andersen@example.com",
        "phone": "+12345678910",
        "zipcode": "90210",
        "source": "RE/MAX.com",
        "sub_source": "Listing Inquiry",
        "brokerage_agent_identifier": "1234",
        "brokerage_agent_type": "favourited",
        "brokerage_office_identifier": "5678"
      },
      “reassigned_at": "2013-11-01 20:35:49"
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "reassign_lead"</td>
  </tr>
  <tr>
    <td>reassign.lead.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>reassign.lead.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>reassign.lead.zipcode</td>
    <td>string</td>
    <td>Zip code for the inquiry</td>
  </tr>
  <tr>
    <td>reassign.lead.source</td>
    <td>string</td>
    <td>the origin of the lead (Remax,Realtor and others)</td>
  </tr>
  <tr>
    <td>reassign.lead.sub_source</td>
    <td>string</td>
    <td>the secondary origin of the lead (Listing Inquiry, Agent Profile etc)</td>
  </tr>
  <tr>
    <td>reassign.lead.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>reassign.lead.brokerage_agent_type</td>
    <td>string</td>
    <td>type of routing for the agent e.g. "favourited","connected" etc</td>
  </tr>
  <tr>
    <td>reassign.lead.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>reassign.reassigned_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
</table>

## Select Possible Offices

This event will return the offices in the selection pool for a particular zip code for auditing purposes.
''offices'' is the collection of offices in a particular zipcode available in the pool for assignment

```
{
    "meta": {
        "event_type": “select_possible_offices"
    },
    “possible_offices": {
        “zipcode": "90210",
        “retrieved_at": "2013-11-01 20:35:49",
        “offices": [
            {
                "id": “12354",
                “weight": 0.75
            },
            {
                "id": “56474",
                “weight": 0.25
            }
        ]
    }
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
    <td>meta.select_possible_offices</td>
    <td>string</td>
    <td>Possible value: "select_offices"</td>
  </tr>
  <tr>
    <td>possible_offices.zipcode</td>
    <td>string</td>
    <td>Zip code for the inquiry</td>
  </tr>
  <tr>
    <td>possible_offices.retrieved_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
  <tr>
    <td>possible_offices.offices.id</td>
    <td>string</td>
    <td>office id provided by the broker</td>
  </tr>
  <tr>
    <td>possible_offices.offices.weight</td>
    <td>float</td>
    <td>office weighting provided by the broker</td>
  </tr>
</table>

## Error assigning lead

This event will indicate that there was an error received from FiveStreet assigning the lead

```
{
    "meta": {
        "event_type: "error_assigning_lead"
    },
    “error": {
      “lead": {
        "name": "James Andersen",
        "email": "james.andersen@example.com",
        "phone": "+12345678910",
        "zipcode": "90210",
        "source": "RE/MAX.com",
        "sub_source": "Listing Inquiry",
        "brokerage_agent_identifier": "1234",
        "brokerage_agent_type": "favourited",
        "brokerage_office_identifier": "5678"
      },
      “message": "agent_id not found in FiveStreet",
      “error_received_at": "2013-11-01 20:35:49"
    }
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
    <td>meta.event_type</td>
    <td>string</td>
    <td>Possible value: "reassign_lead"</td>
  </tr>
  <tr>
    <td>error.lead.name</td>
    <td>string</td>
    <td>full name</td>
  </tr>
  <tr>
    <td>error.lead.email</td>
    <td>string</td>
    <td>agent's email</td>
  </tr>
  <tr>
    <td>error.lead.zipcode</td>
    <td>string</td>
    <td>Zip code for the inquiry</td>
  </tr>
  <tr>
    <td>error.lead.source</td>
    <td>string</td>
    <td>the origin of the lead (Remax,Realtor and others)</td>
  </tr>
  <tr>
    <td>error.lead.sub_source</td>
    <td>string</td>
    <td>the secondary origin of the lead (Listing Inquiry, Agent Profile etc)</td>
  </tr>
  <tr>
    <td>error.lead.brokerage_agent_identifier</td>
    <td>string</td>
    <td>agent account identifier provided by broker</td>
  </tr>
  <tr>
    <td>error.lead.brokerage_agent_type</td>
    <td>string</td>
    <td>type of routing for the agent e.g. "favourited","connected" etc</td>
  </tr>
  <tr>
    <td>error.lead.brokerage_office_identifier</td>
    <td>string</td>
    <td>agent office identifier provided by broker</td>
  </tr>
  <tr>
    <td>error.message</td>
    <td>string</td>
    <td>Description of the error received from FiveStreet</td>
  </tr>
  <tr>
    <td>error.error_received_at</td>
    <td>string</td>
    <td>Date represented as a string; format: yyyy-mm-dd hh:mm:ss</td>
  </tr>
</table>
