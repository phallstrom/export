## Python Export script for TempoDB

This Python script exports the complete contents of your TempoDB database. It creates a directory with the following:
* A file, `series_info`, with a JSON representation of each series, including series key, tags, attributes, and a client-generated UUID. 
* For each series, a file `<UUID>.csv` with the raw data points for the corresponding series. Each CSV line contains two fields: an ISO 8601-formatted timestamp, and a value.
 
Parameters are included in the head of the file:
* **EXPORT_DIR** - name of the directory to output into. Relative to the current directory.
* **API_KEY**, **API_SECRET** - TempoDB credentials, can be found at  https://tempo-db.com/manage/
* **START_DATE**, **END_DATE** - Only data points within this range will be exported. There's no problem with specifying this much wider than your actual data range.
 
Note that this script requires the latest version of TempoDB's Python client, available here: https://github.com/tempodb/tempodb-python/tree/v1.0

## Ruby Export script for TempoDB

This Ruby script exports the complete contents of your TempoDB database. It creates a directory for each series with the following:
* A file, `meta.json`, with a JSON representation of the series meta data (id, key, attributes, tags, etc.). 
* A file `data.csv` with the raw data points for the corresponding series. Each CSV line contains two fields: an ISO 8601-formatted timestamp, and a value.

Note that this script requires the following ruby gems: tempodb, json, csv.

### Usage

    TDB_EXPORT_DIR='export' TDB_START='2013-01-01' TDB_END='2014-12-31' TDB_DATABASE_ID='...' TDB_API_KEY='...' TDB_API_SECRET='...' ruby export.rb
