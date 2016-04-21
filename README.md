#WeDigBio Dashboard Features:

* Maps of cumulative participant activity across project and events    
Example: [Torque Map](https://www.wedigbio.org/content/transcription-activity-map)
* Heat-map of collection localities transcribed
* Stream of thumbnail images that have been transcribed 
* Timeline of transcribed records by collection date
* Leaderboard

_Dashboard endpoints should be structured something like this:_
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
      "decimalLatitude": "Lat. of collecting event",
      "decimalLongitude": "Long. of collecting event",
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


##Metadata



##Current Dashboard Data Providers


