#WeDigBio Dashboard Features:

* Maps of cumulative participant activity across project and events
Example: [Torque Map](https://www.wedigbio.org/content/transcription-activity-map)
* Heat-map of collection localities transcribed
* Stream of thumbnail images that have been transcribed
* Timeline of transcribed records by collection date
* Leaderboard

_Dashboard endpoints should be structured something like this and should default to the current timestamp and sort in descending order by timestamp:_
```json
{
  "numFound":"",
  "start":"",
  "rows":"",
  "items": [{
    "project": "Project name, if more than one project on this feed",
    "description": "Description of transcription event, might include Specimen name or Collector Name/Collection Name or Collection ID",
    "guid": "Unique identifier for this event",
    "timestamp": "Timestamp of transcription",
    "subject": {
      "link": "Specimen page URI (on transcribing site)",
      "thumbnailUri": "Thumbnail URI",
    },
    "contributor": {
      "decimalLatitude": "",
      "decimalLongitude": "",
      "ipAddress": "IP",
      "transcriber": "User or project who created this transcription",
      "physicalLocation": {
        "country": "",
        "province": "",
        "county": "",
        "municipality": "",
        "locality": ""
      }
    },
    "transcriptionContent": {
      "lat": "",
      "long": "",
      "country": "",
      "province": "",
      "county": "",
      "municipality": "",
      "locality": "",
      "date": "",
      "collector":"",
      "taxon":"",
    },
    "discretionaryState": "Project-specific detail about state"
  }]
}
```
_endpoints should accept the following parameters:_
  * ?timestampStart = UTC timestamp (optional)
  * ?timestampEnd = UTC timestamp (optional)
  * ?rowStart = int  (optional, used in paging, row number to start from)

##Metadata

```numFound```: Number of objects that match the current query  
```start```: This parameter is used to paginate results from a query. When specified, it indicates the offset in the complete result set for the queries where the set of returned objects should begin. (i.e. the first record appear in the result set is the offset)  
```rows```: This parameter is used to paginate results from a query. It specify the maximum number of objects from the complete result set to return to the client for every request.   
```items```: This object is the payload element of enpoint and each item object should represent some unit of transcription effort.  
```contributor```: The contributor object is a property of the item object and is used to communicate information about the individual or group performing the transcription activity. 
```transcriptionContent```: This object should contain the results of, or data created by, the transcription activity. 
```discretionaryState```: This object should be used to communicate project-specific information about the transcription activity. ie Unit of effort, completion flag, validation flag, etc 


##Current Dashboard Data Providers

###DigiVol:http://volunteer.ala.org.au/ws/transcriptionFeed.json
accepts `dateStart`, `dateEnd` and `rowStart` query params  
`dateStart` and `dateEnd` can be unix time, java time or a iso 8601 formatted timestamp string (aka JS Date.toJSON() format

###Les Herbonautes:http://lesherbonautes.mnhn.fr/contributions/interval/json
