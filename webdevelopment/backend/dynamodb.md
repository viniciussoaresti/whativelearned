# DynamoDB:
## Introduction:
It's a nosql DB that's fast. And that's about it. Yes, i've just copied and pasted the 'aws.md' text.
## Inside DynamoDB:
It works with tables (e.g. people), items (e.g. person) and attributes (e.g. name).
Each item has a primary key.
Note that each item can have a different number and types of attributes.
### About Primary Keys:
- Partition Key: A simple primary key.
- Partition and Sort Keys (a.k.a Composite Key): This makes the items with the same partition key to be stored together. This type of definition gives flexibility on querys.
### Secondary Indexes:
You can create indexes to query with other attributes.
### Streams:
A feature that captures data modification events on tables.
It records added, modified and deleted items.
Why? e.g.(Create a Lambda Trigger when a new user is added.)
## Commands:
- CreateTable (you can create 1+ index(es) and enable Streams);
- DescribeTable: Returns information about a table, such as its primary key schema, throughput settings, and index information;
- ListTables;
- UpdateTable (update table settings, create indexes);
- DeleteTable;
- PutItem (you have to specify the primary key attributes);
- BatchWriteItem: inserts up to 25 items on 1+ tabçes;
- GetItem (you must specify the primary key, and you can retrieve just a subset of the attributes);
- BatchGetItem: retrieves up to 100 items (detail: from one or more tables);
- Query: Retrieve all items with the same partition key, complete or only with some attributes, apply conditions to filter them. It can be used on a table and on a index.
- Scan: Retrieve all items on a table or index. It can be filtered too.
- UpdateItem: You can add, modify and delete attributes. It can perform conditional updates and an atomic counter;
- DeleteItem;
- BatchWriteItem: Yes, the same command again. Surprise! It can also be used to delete items. Yes, same 25. 1+ Tables.
- ListStreams;
- DescribeStream;
- GetShardIterator: Returns a shard iterator, which is a data structure that your application uses to retrieve the records from the stream;
- GetRecords: Retrieves one or more stream records, using a given shard iterator;
- TransactWriteItems: A batch operation that allows Put, Update, and Delete operations to multiple items both within and across tables with a guaranteed all-or-nothing result;
- TransactGetItems: A batch operation that allows Get operations to retrieves multiple items from one or more tables.
## Data Types for Attributes:
- Scalar (a value);
- Document: a complex structure, like a Json. There are two types: List and Map;
- Set: multiple scalar values (an array). It can be a String, Number or Binary Set.
### Scalar:
Number (38 digits precision), String, Binary (base64 encoded values), Boolean and Null.
### Document:
- List (like a JSON array, eg.: (FavoriteThings: ["Cookies", "Coffee", 3.14159]));
- Map (like a JSON object, e.g.: ({Day: 'monday', Something: 'idk'})).
### Set:
A JSON array.
## Capacity Mode:
In summary, on-demand and provisioned (fixed) bandwith can be defined, considering:
- 1 Read Capacity Unit (RCU): One strongly (== 2 eventually) consistent read per second for an item up to 4kb;
- 1 Write Capacity Unit (WCU): One strongly (== 2 eventually) consistent write per second for an item up to 1kb.
## Actual Usage (examples):
### Creating Table Example (parameter):
```
{
    TableName : "Music",
    KeySchema: [       
        { 
            AttributeName: "Artist", 
            KeyType: "HASH", //Partition key
        },
        { 
            AttributeName: "SongTitle", 
            KeyType: "RANGE" //Sort key
        }
    ],
    AttributeDefinitions: [
        { 
            AttributeName: "Artist", 
            AttributeType: "S" 
        },
        { 
            AttributeName: "SongTitle", 
            AttributeType: "S" 
        }
    ],
    ProvisionedThroughput: {       // Only specified if using provisioned mode
        ReadCapacityUnits: 1, 
        WriteCapacityUnits: 1
    }
}
```
### Describe Table Example (parameter):
```
{
    TableName : "Music"
}
```
### Write Data Example (parameter for putitem):
```
{
    TableName: "Music",
    Item: {
        "Artist": "The Acme Band",
        "SongTitle": "Look Out, World",
        "AlbumTitle":"The Buck Starts Here",
        "Price": 0.99,
        "Genre": "Rock"
    }
}
```
### Read Data Examples (parameters):
#### ReadItem:
```
{
    TableName: "Music",
    Key: {
        "Artist": "No One You Know",
        "SongTitle": "Call Me Today"
    },
    "ProjectionExpression": "AlbumTitle, Year, Price"
}
```
#### Query (parameter):
```
// Return all of the songs by an artist, matching first part of title

{
    TableName: "Music",
    KeyConditionExpression: "Artist = :a and begins_with(SongTitle, :t)",
    ExpressionAttributeValues: {
        ":a": "No One You Know",
        ":t": "Call"
    }
}
```
#### Scan (parameter):
```
// Return all of the values for Artist and Title
{
    TableName:  "Music",
    ProjectionExpression: "Artist, Title"
}
```
Important:
- The Scan action also provides a FilterExpression parameter, which you can use to discard items that you do not want to appear in the results. A FilterExpression is applied after the entire table is scanned, but before the results are returned to you. (This is not recommended with large tables. You are still charged for the entire Scan, even if only a few matching items are returned.)
### Indexes:
There are two kinds:
- Global: The primary key of the index can be any two attributes from its table;
- Local: The partition key of the index must be the same as the partition key of its table. However, the sort key can be any other attribute.
#### Example adding a global secondary index to an existing table, using the UpdateTable action and specifying GlobalSecondaryIndexUpdates:
```
{
    TableName: "Music",
    AttributeDefinitions:[
        {AttributeName: "Genre", AttributeType: "S"},
        {AttributeName: "Price", AttributeType: "N"}
    ],
    GlobalSecondaryIndexUpdates: [
        {
            Create: {
                IndexName: "GenreAndPriceIndex",
                KeySchema: [
                    {AttributeName: "Genre", KeyType: "HASH"}, //Partition key
                    {AttributeName: "Price", KeyType: "RANGE"}, //Sort key
                ],
                Projection: {
                    "ProjectionType": "ALL"
                },
                ProvisionedThroughput: {                                // Only specified if using provisioned mode
                    "ReadCapacityUnits": 1,"WriteCapacityUnits": 1
                }
            }
        }
    ]
}
```
#### Querying an index:
```
// All of the rock songs

{
    TableName: "Music",
    IndexName: "GenreAndPriceIndex",
    KeyConditionExpression: "Genre = :genre",
    ExpressionAttributeValues: {
        ":genre": "Rock"
    },
};
```
### Modyfying Data (parameter for updateitem, can also have atomic counters and incrementers):
```
{
    TableName: "Music",
    Key: {
        "Artist":"No One You Know",
        "SongTitle":"Call Me Today"
    },
    UpdateExpression: "SET RecordLabel = :label",
    ConditionExpression: "Price >= :p",
    ExpressionAttributeValues: { 
        ":label": "Global Records",
        ":p": 2.00
    }
}
```
### Deleting Data (parameter):
```
{
    TableName: "Music",
    Key: {
        Artist: "The Acme Band", 
        SongTitle: "Look Out, World"
    }
}
```
### Removing a Table (parameter):
```
{
    TableName: "Music"
}
```