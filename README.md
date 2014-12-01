# jsontsv

NOT IN WORKING STATE; IN PROGRESS.

A simple tool to transform JSON into tab-separated line-oriented output
amenable to Unix text processing. 

Input should be a stream of JSON objects with mostly uniform keys.

Output keys must be specified. If none are specified, all the top-level keys of
the first object are taken as the template.


  jsontsv '.title .rating .url' < input.json


Terminal values. If the key maps to a scalar value or Null, it is printed to
the column. 

If it any key in a series maps to an array, and it is the last key, the values
are output separated by ",". If key is not the final key, the following keys
are mapped to the objects that assumed to populate the array.

## Nested keys

  jsontsv 'title duplicates.Rental.HD duplicates.Rental.SD' < input.json


## Column names

Column names are simply the keypaths

## Using a file to designate columns:

  jsontsv -f keys  < input.json

## Indicating presence

Appending a question mark, e.g.

  .title? 

will output T if present, F is not present

## Concatenating fields, truncating fields, etc.

This should be done downstream using a tool like AWK.

