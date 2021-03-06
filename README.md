# gavagai-python
A Gavagai API helper library.

## Install

```bash
$ pip install gavagai
```

## Api key
Get your own api key for free at [Gavagai Developer Portal](https://developer.gavagai.se).

The api key can be specified when instantiating the client, see examples below. Alternatively, you can set the GAVAGAI_APIKEY environment variable, and just call `GavagaiClient()`.

## Use
See [Gavagai API documentation](https://developer.gavagai.se/docs) for details about available API resources.

### Straight API call
The `/keywords` resource extracts salient concepts from a collection of texts. Order by number of occurrences.

```python
from gavagai.client import GavagaiClient
from pprint import pprint

texts = [
    'Stayed here for 3 nights at the beginning of a trip of California. Could not say enough good things about the hotel Monaco. Amazing staff, amazing rooms and the location is brilliant! First stay at a Kimpton hotel, but definitely not the last!!!',
    'I did a lot of research looking for a hotel suite for our family vacation in San Francisco. The Hotel Monaco was a perfect choice. What friendly and delightful staff. I will miss the Grand Cafe, but I will make sure to come back to see their new offerings.',
    'My partner and I spent four nights here over New Years and loved it. Super staff; lovely, quiet room; excellent location within easy walking to much of Downtown and an overall experience that was perfect.'
]

client = GavagaiClient('use_your_own_api_key')
result = client.keywords(texts)
keywords = result.json()

pprint(keywords)
```

### API call with additional options

The `/tonality` resource measures multi-dimensional sentiment, based on lexical analysis. For accuracy, language should be specified.

```python
rom gavagai.client import GavagaiClient
from pprint import pprint

texts = [u'Din idiot!', u'Jag älskar dig.', u'Hen hatar det.']

client = GavagaiClient('use_your_own_api_key')
result = client.tonality(texts, language='sv')
keywords = result.json()

pprint(keywords)
```


## Set up for development
From root of this repository: 

```bash
$ pip install -r requirements.txt
```

## Run tests

```bash
$ py.test
```