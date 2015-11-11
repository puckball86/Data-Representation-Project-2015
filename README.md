## Data Representation and Querying Project 2015

### Student Name: Dara Starr G00209787

## Introduction
This project provides the design and documentation for the dataset "Leases surrendered in 2009" which is available at (https://data.gov.ie/dataset/leases-surrendered-in-2009). The host I am using for this project is dara.starr.info.


##Json Code

[
  {
    "COUNTY": "CORK",
    "BUILDING": "Clonakilty Temp Decent Offices",
    "ADDRESS 1": "West Cork Technology Park",
    "NET LETT SqM": 869.84,
    "RENT PA": 118910
  },
  
  {
    "COUNTY": "CORK",
    "BUILDING": "Clonakilty Temp Decent Offices",
    "ADDRESS 1": "West Cork Technology Park",
    "NET LETT SqM": 0,
    "RENT PA": 157480
  },
]
..........etc


##Possible requests
###"GET"
A GET request is possible using http://dara.starr.info/leases?COUNTY=Limerick&NET_LETT_SqM=492.
parameters{:COUNTY/NET_LETT_SqM}
validation {String single word} : {integer}

This will return all the leases from Limerick that also have the size of 492 meters squared. The response will be returned in the format of:
    - *county*: the county of the lease.
    - "building": the name of the building.
    - "address 1": the street where the lease is located.
    - *nett lett sqm*: the size of the car.
    - "rent pa": the annual rent of the lease.

       GET /leases?COUNTY=LIMERICK&NET_LETT_SqM=492HTTP/1.1
        Host: dara.starr.info
        Cache-Control: no-cache

This is the sample output from the parametrized GET request.
{
    "COUNTY": "LIMERICK",
    "BUILDING": "Limerick Estuary House",
    "ADDRESS_1": "Henry Street",
    "NET_LETT_SqM": 492,
    "RENT_PA": 68771
  },

###"POST"
Performing a POST request on http://dara.starr.info/leases/

POST /leases/ HTTP/1.1
Host: dara.starr.info
Cache-Control: no-cache
Content-Type: multipart/form-data;
 
Content-Disposition: form-data; name="COUNTY" value="CORK"
Content-Disposition: form-data; name="BUILDING" value="Cork Appartment Complex"
Content-Disposition: form-data; name="ADDRESS_1" value="McCurtain Street"
Content-Disposition: form-data; name="NET_LETT_SqM" value="580"
Content-Disposition: form-data; name="RENT_PA" value="12000"

{
    "COUNTY": "CORK",
    "BUILDING": "Cork Appartment Complex",
    "ADDRESS_1": "McCurtain Street",
    "NET_LETT_SqM": 580,
    "RENT_PA": 12000
  },

PUT



DELETE
