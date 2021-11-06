---
description: Importing files _without_ Pandas
---

There are a lot of different types of files.  This is the way to interact with a lot of those files, focusing on local files (not API calls)


### Opening Basic Files

This one is pretty straight forwards.

```python
# Reading a file; do this unless you're editing it
with open('real_cool_document.txt') as cool_doc:
  cool_contents = cool_doc.read()
  print(cool_contents)

# Or for just the top line, to preserve performance
with open('just_the_first.txt') as first_line_doc:
  first_line = first_line_doc.readline()
  print(first_line)

# Writing to a file
with open('bad_bands.txt', 'w') as bad_bands_doc:
  bad_bands_doc.write('Nickelback')

# Opening and appending to a file
with open('cool_dogs.txt', 'a') as cool_dogs_file:
  cool_dogs_file.write("Air Buddy")
```

### CSV Fiddling

Unerringly, `pandas` tends to do this better, but for the sake of completeness, here's how to do it with `csv`.  It's a lower-level library and allows for iteration in case the data is truly terrible.

```python
import csv

# Same as above, how to open...
with open('cool_csv.csv') as cool_csv_file:
  cool_csv_dict = csv.DictReader(cool_csv_file)
  for row in cool_csv_dict:
    print(row['Cool Fact'])


```

Writing to a .csv...

```python
access_log = [{'time': '08:39:37', 'limit': 844404, 'address': '1.227.124.181'}, {'time': '13:13:35', 'limit': 543871, 'address': '198.51.139.193'}, {'time': '19:40:45', 'limit': 3021, 'address': '172.1.254.208'}, {'time': '18:57:16', 'limit': 67031769, 'address': '172.58.247.219'}, {'time': '21:17:13', 'limit': 9083, 'address': '124.144.20.113'}, {'time': '23:34:17', 'limit': 65913, 'address': '203.236.149.220'}, {'time': '13:58:05', 'limit': 1541474, 'address': '192.52.206.76'}, {'time': '10:52:00', 'limit': 11465607, 'address': '104.47.149.93'}, {'time': '14:56:12', 'limit': 109, 'address': '192.31.185.7'}, {'time': '18:56:35', 'limit': 6207, 'address': '2.228.164.197'}]
fields = ['time', 'address', 'limit']

import csv

with open('logger.csv', 'w') as logger_csv:
  log_writer = csv.DictWriter(logger_csv, fieldnames=fields)
  log_writer.writeheader()
  for log in access_log:
    log_writer.writerow(log)

```


### Freaking JSON

I hate JSON because it's not a relational database.  It's annoying, and perpeptually object-oriented despite mainly being implemented in bloody functional programming sets.  Here's how you deal with it anyway, sorry you're here again future Katt.


##### Opening JSON

```purchase_14781239.json
{
  'user': 'ellen_greg',
  'action': 'purchase',
  'item_id': '14781239',
}
```

```python
import json
 
with open('purchase_14781239.json') as purchase_json:
  purchase_data = json.load(purchase_json)
 
print(purchase_data['user'])
# Prints 'ellen_greg'
```


##### Adding to JSON

```python
data_payload = [
  {'interesting message': 'What is JSON? A web application\'s little pile of secrets.',
   'follow up': 'But enough talk!'}
]

import json

with open('data.json', 'w') as data_json:
  json.dump(data_payload, data_json)
```


