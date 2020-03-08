# Art Music Curation in Australia Dataset

This dataset contains comprehensive logs, comprising 982,182 records of music presented on three platforms:
- **ABC Classic FM radio broadcasts** (1998-2018)
- **Concert events catalogued by the Australian Music Centre** (2009-2018)
- **Classical genre Spotify playlists entries** (Jan - May 2018)

The raw data has been harvested, transformed and classified at the level of the individual composer whose music was featured in each discrete broadcast or presentation.

Composer attributes recorded for each content item include:
- Name
- Year of birth
- Gender
- Place of activity (including state, country and continent)
- Spotify artist identifier
- Spotify popularity score (as of August 2017)
- iTunes artist identifier

Each discrete content item includes details on:
- The context in which the item was featured (e.g. the radio program, concert program, or Spotify playlist)
- The sequential order in which it was presented
- The date and time of presentation
- The duration of the item

The concert data also includes the following information on each of the performers:
- Name
- Gender
- Year of birth
- Size of the performing ensemble
- Repertoire focus of the performing ensemble

## Data Files
The data is provided in this repository as two tab-separated UTF8 text files:
- amca_dataset_content-items_20200308.txt
- amca_dataset_performer_20200308.txt

A header row in each file includes field names corresponding to the data dictionaries detailed below.


### #1 Content Items
Each row represents a content item featured on one of the three platforms

**Filename**: amca_dataset_content-items_20200308.tar.gz

**Records**: 982,182


Field | Type | Description
--- | --- | ---
platform | Text | The media platform for the content item: one of ‘broadcast’, ‘playlist’ or ‘concert’.
id | Integer | An integer which uniquely identifies each content item within other content items from the same platform.
sequence | Integer | The order in which the current item appears in its parent context. For radio broadcasts this number increments for each item in the entire dataset. For playlists entries, this number reflects the position of the record in the playlist in which it was featured. Sequence data is not available for concert records.
context | Text | The context in which the content item was featured. For radio broadcasts, this reflects the radio program. For playlists items, it is the name of the playlist. For concerts it is a hash which reflects an individual concert program.
date | Date | The date on which the context item was presented. For radio broadcasts, this reflects the broadcast date. For playlist entries it is the date the version of the playlist was published. For concerts it is the year in which the concert program was presented.
time | Time | The time of day at which the context item was presented.
duration | Integer | The duration of the content item in seconds.
raw_composer | Text | The name of the composer of the content item, as it appeared in the raw data source and before matching to a canonical entry.
composer | Text | The canonical name of the composer of the content item, after matching to authoritative data
yob | Integer | Year of birth of the composer of the content item.
gender | Text | Gender of the composer of the content item.
place | Text | Place where the composer of the content item was principally active.
country | Text | Maps the specific location recorded in the place field to a country.
continent | Text | Maps the specific location recorded in the place field to a continent.
state | Text | Maps the specific location recorded in the place field to an Australian state or territory.
spotify_artist_id | Text | The Spotify artist identifier for the composer of the content item.
spotify_popularity | Integer | The popularity score for the composer of the content item, as obtained from Spotify’s API in August 2017.
spotify_followers | Integer | The number of followers for the composer of the content item, as obtained from Spotify’s API in August 2017.
itunes_artist_id | Integer | The iTunes artist identifier for the composer of the content item.
spotify_track_id | Text | The Spotify track identify for the content item work. Only available for playlist content items.


### #2 Performers
Each row represents a content item featured on one of the three platforms

**Filename**: amca_dataset_performers_20200308.tar.gz

**Records**: 34,908

Field | Type | Description
--- | --- | ---
content_item_platform | Text | References the platform field of the Content Items file. Together with the id field, this defines a foreign key relationship.
content_item_id | Integer | References the id field of the Content Items file.
name | Text | The name of the performer.
gender | Text | The gender of the performer.
yob | Integer | The year of birth of the performer.
performer_size | Text | A classification of the size of the performer entity. One of: Accompanist, Composer-as-performer, Soloist, Small [2-4 players], Medium [5-11 players], Large [12+ players].
performer_repertoire_focus | Text | A classification of the general repertoire focus of the performer entity. One of: Heritage, Mixed, Contemporary.
