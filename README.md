#**Data Representation and Querying Project 2015**

##**Student Name:** Dara Starr G00209787

###**Introduction**

This project provides the design and documentation for the dataset "Leases surrendered in 2009" which is available at (https://data.gov.ie/dataset/leases-surrendered-in-2009). The host I am using for this project is (https://dara.starr.info/v0/)

###**About The Data**
This dataset was received in Comma Separated Values (CSV) format, and was downloaded from [*data.gov.ie*](https://data.gov.ie/dataset/leases-surrendered-in-2009).
The CSV file contains 36 rows, the first being a header row with the names of each field.
There are five values on each line, which are as follows:

**COUNTY**: This is the county in which the lease is located. 

    validation:{String}

**BUILDING**: This is the name of the building.

    validation:{String}

**ADDRESS_1**: This is the address at which the lease is located.

    validation:{String}

**NET LETT SqM**: This is the size of the lease.

    validation:{int}

**RENT PA**: This is the amount the lease cost per annum.

    validation:{int}


###**Example Json Code**

      [ 
      {
        "COUNTY": "CORK",
        "BUILDING": "Clonakilty Temp Decent Offices",
        "ADDRESS 1": "West Cork Technology Park",
        "NET LETT SqM": 869.84,
        "RENT PA": 118910
      },
      {
        "COUNTY": "TIPPERARY",
        "BUILDING": "Thurles Justice Welfare Office",
        "ADDRESS 1": "Teach an Chuinne",
        "NET LETT SqM": 74.32,
        "RENT PA": 10729.29
      },] ..........etc

###**Possible requests**
**GET**: A read representation of a specific resource
**POST**: Create or update without a known ID
**PUT** :Update of create with a known ID
**DELETE**: Remove




###***GET***

A **GET** request is possible using https://dara.starr.info/v0/leases?COUNTY=Limerick&NET_LETT_SqM=492. parameters `{COUNTY/NET_LETT_SqM}` 
validation `{String single word} : {integer}`

This will return all the leases from Limerick that also have the size of 492 meters squared. The response will be returned in the format of:
 - "COUNTY": the county of the lease.
 - "BUILDING": the name of the building. 
 - "ADDRESS_1": the street where the lease is located. 
 - "NET_LETT_SqM": the size of the car. 
 - "RENT_PA": the annual rent of the lease.

  

     GET /leases?COUNTY=LIMERICK&NET_LETT_SqM=492HTTP/1.1
        Host: dara.starr.info
        Cache-Control: no-cache

This is the sample output from the parametrized GET request. 

    {
        "COUNTY": "LIMERICK",
        "BUILDING": "Limerick Estuary House",
        "ADDRESS 1": "Henry Street",
        "NET LETT SqM": 492,
        "RENT PA": 68771
      },

A **GET** request using https://dara.starr.info/v0/leases?COUNTY=Westmeath

    GET /leases?COUNTY=WESTMEATHHTTP/1.1
            Host: dara.starr.info
            Cache-Control: no-cache

###**RESPONSE**
    {
        "COUNTY": "WESTMEATH",
        "BUILDING": "Mullingar Vehicle Reg Office",
        "ADDRESS 1": "Spout Well Lane",
        "NET LETT SqM": 74.32,
        "RENT PA": 14500
      },

###***POST***

Performing a POST request on http://dara.starr.info/v0/leases/.
This will create a record. We assign new values to each of the fields. This is what the request will look like and underneath is the json that will be displayed.

     POST /leases/ HTTP/1.1 Host: dara.starr.info 
     Cache-Control: no-cache 
     Content-Type: multipart/form-data;
     
     Content-Disposition: form-data; name="COUNTY" value="Cork"   
     Content-Disposition: form-data; name="BUILDING" value="Cork Appartment Complex"
     Content-Disposition: form-data; name="ADDRESS_1" value="McCurtain Street"
     Content-Disposition: form-data; name="NET_LETT_SqM" value="492"
     Content-Disposition: form-data; name="RENT_PA" value="12000"

###json after post
      [
      {
        "COUNTY": "CORK",
        "BUILDING": "Cork Appartment Complex",
        "ADDRESS 1": "McCurtain Street",
        "NET LETT SqM": 580,
        "RENT PA": 12000
      },]
