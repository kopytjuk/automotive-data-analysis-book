# Data representation

This chapter gives a rough overview of data formats often used in automotive industry for recordings,
analysis and exchange.

## Taxonomy

### Record vs. column based

In a column-wise representation, each column of data is stored together, 
such that all the values for a given attribute (e.g., age, name, address) are stored in the same column.
This can be useful for analysis, as it allows for easy aggregation and filtering of data based on specific attributes.

In contrast, in a record-wise representation, each row of data is stored together, 
such that all the attributes for a given entity (e.g., person, product, transaction) are stored in the same row. 
This can be useful for viewing and editing individual records,
as all the information about a given entity is presented together in one place.

A good discussion about the representation can be found on [StackOverflow](https://stackoverflow.com/a/36831549/10251805).

### Character-based vs. binary

Character based formats, represent the data as ASCII characters, so they can directly interpreted by humans in
a text editor.

Contrary to that, a binary type cannot be opened in a text editor and interpreted by a 
human due to binary representation of the numbers (instead of characters in ASCII) and in some cases
applied compression.

## Character-based formats

### CSV

CSV stands for "Comma-Separated Values", and it is a simple file format used to store tabular data (data organized in rows and columns).

In a CSV file, each row represents a record, and each column represents a field. Fields are separated by a delimiter, most commonly a comma (hence the name). 
However, other delimiters such as semicolons or tabs can also be used.

The first row of a CSV file often contains the names of the fields (also called headers), while the subsequent rows contain the actual data.

```csv
time_ms, object_id, x, y, z
1678554731011, 40, 74.2, 3.51, -0.03
1678554731011, 42, 69.2, 0.12, 0.02
1678554731022, 40, 73.6, 3.48, 0.022
1678554731022, 42, 73.8, -0.15, -0.031
...
```

CSV files are commonly used to exchange data between different software applications because they are simple and easy to read and write. A big advantage of them is being easily readable by a human for short plausibility checks. In parallel computing, the line-delimited structure allows an easier distribution to multiple computing threads (e.g. CPU-cores, processors, virtual machines).

However, they have some limitations, such as being memory intensive (a number `1678554731022` has to be represented with 13 bytes with a byte per character.) By nature, since CSV represents tabular data, it is not able to represent complex data structures such as graphs or list of lists.
Also, containing special characters (without encoding information from the author) that can cause issues when importing or exporting data.

### JSON

JSON stands for "JavaScript Object Notation", and it is a lightweight data interchange format used to store and exchange structured data between different software applications. In a JSON file, data is represented as key-value pairs `{"key": value}` or as an ordered list of values. JSON is based on a subset of the JavaScript programming language syntax but is independent of any programming language.

JSON files use a simple and intuitive syntax that is easy for humans to read and write. JSON files consist of objects enclosed in curly braces `{}` and arrays enclosed in square brackets `[]`. An object contains a set of key-value pairs, while an array contains an ordered list of values:

```json
{
    "records": [
            {
                "time_ms": 1678554731011, 
                "objects": [
                    {"id": 40, "x": 74.2, "y": 3.51, "z": -0.03},
                    {"id": 42, "x": 69.2, "y": 0.12, "z": 0.02}
                ]
            },
            {
                "time_ms": 1678554731022, 
                "objects": [
                    {"id": 40, "x": 73.6, "y": 3.48, "z": 0.022},
                    ...
                ]
            },
        ]
}
```

JSON files are commonly used in Web-technology to transmit data between a server and a web application, but they can also be used to store configuration data or other structured data types. It is supported by most modern programming languages and can be easily parsed and generated using libraries or built-in functions.

Although JSON has many advantages, it also has some disadvantages:

- Limited data types: JSON supports only a limited set of data types, such as strings, numbers, boolean values, and null. This means that more complex data structures, such as dates or binary data, need to be encoded or decoded using workarounds.

- Large file sizes: In some cases, JSON files can be larger than other data formats, such as CSV, because of its verbose nature. This can lead to slower data transfers or larger loading times.

A notable extension of JSON is JSONL, which stands for Line delimited JSON, where each line represents a single record (e.g. point in time).

### XML, YAML, INI, .env ...

There are many other formats used in web & OS technology and are still existing in many software tools used in automotive industry. 
Often they do not hold large arrays of data such hour long recordings with many variable, rather they are used as configuration files. There are some advantages and disadvantages compared to JSON, such as schema checks for XML or support for comments in YAML and `.env` files.

When you design a complex system with external configuration, consider your stakeholders (users, consumers) and software interacting with your system in your choice.

## Binary formats

Binary formats have multiple advantages over text-based formats.
In addition to the memory efficiency (i.e. floating point number as a 64-bit vs. multiple ASCII characters), 
the values binary formats store are often *typed*, means there is only one
way to store and interpret for client applications. This allows a more robust data-exchange and data management.

### Spreadsheet formats (xlsx, odt)

TODO

### ASAM MDF

MDF (Measurement Data Format) is a binary file format to store recorded or calculated data for post-measurement processing,
off-line evaluation or long-term storage. The format has become a de-facto standard for measurement & calibration systems (MC-systems), 
but is also used in many other application areas.

### Parquet

Apache Parquet is a free and open-source column-oriented data storage format coming from the Apache Hadoop ecosystem[^parquet-wiki].

The values in each column are stored in contiguous memory locations, providing the following benefits[^parquet-wiki]:

- Column-wise compression is efficient in storage space[^parquet-file-format]
- Encoding and compression techniques specific to the type of data in each column can be used
- Queries that fetch specific column values need not read the entire row, thus improving performance

### Protobuf (WIP)

### ROS messages (WIP)

### Avro (WIP)

Avro is a row-based storage format for Hadoop.

### Custom (WIP)

Proprietary binary formats ...

## References

[^parquet-wiki] Wikipedia *Apache Parquet*, [link](https://en.wikipedia.org/wiki/Apache_Parquet)
[^parquet-file-format] Apache Parquet - File Format [link](https://parquet.apache.org/docs/file-format/)
