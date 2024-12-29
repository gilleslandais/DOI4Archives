# Linked Data

DataCite provides a list of controled vocabulary that allows to specify the relationship between resources.
These relations may use DOI or any other sustainable identifier (eg: bibcode).

```
The relatsionship vocabulary is precise.
Too often, providers give their own interpretation of the terms.
If there's any doubt about the meaning of the vocabulary,
it's better to put no relations than a misunderstood relationship.
```

See relation vocabulary and their definitions in the [DataCite Schema](https://datacite-metadata-schema.readthedocs.io/_/downloads/en/4.5/pdf/), section 12


```
Priviledge DOI linking to any relations
```
DOI has to be priviledged than any other identifier or URI. DOI facilitate the harvesting/merging jobs. For instance the EOSC portal selects the relations type to display with and priviledge resources having DOI.

## Link resources within a DataCenter
DataCenter may provides resources in different granularity. For instance Chandra provides catalogue of observations. Each observation is a Product that has his own DOI.
Then the products are linked to the catalogue which has a DOI too.

example: **TODO**

## Link data from outside
There are many reasons to link a resource with external products, we give just few examples:

- link the datasets that have been used to create a product 
- link other copy (term ```isIdenticalTo```)
- for a derived product, link the original data (qualifed terms such as ```isVariantFormOf```, ```isDerivedFrom```, ...)
- cite a resource (term ```Cites```)
- etc.

Example: **TODO**

### Linking Dataset to a publication
DataCites provides terms to link Datasets with articles. For instance ```Cites```, ```isSupplementTo```, ```isDescriebdedBy```, ```References```, etc.
Choosing the good term is specfific to the Datasets. 

Note the ```Cites``` relations which makes an automated citation (the article is cited when the DOI of the dataset is created). 
Other terms like ```References``` generates also statistics in DataCite.

Exemple: 
- get Datacite statistics:  (see "referenceCount", "citationCount")
```
curl "https://api.datacite.org/dois/{DOI}"
```

- get Crossref statistics
```
 curl "https://doi.crossref.org/search/doi?doi=10.3847/1538-4365/ac9af8&format=info&pid=mail@address
```



example: link a dataset with its reference article (vizier DOI extract from https://doi.org/10.26093/cds/vizier.22640008).
The above example provides a relations using a bibcode.

```
"relatedIdentifiers": [
    {
      "relationType": "IsSupplementTo",
      "relatedIdentifier": "2023ApJS..264....8H",
      "relatedIdentifierType": "bibcode"
    }
]
```

### Linking Dataset with its original resource
We distinguish a mirror copy and resource derived from an orginal resource.
Both can have their own DOI. We encourage derived resource as wel as copy mirror to link the original resource using DataCite relations.

There are lots of reasons why a DataCenter that provides a derived resource want to provide a DOI. 
Often, the derived product is the result of a curation that provides added values.

Before creating a DOI, we encourage the DataCenter to tell their DOI plan to the original archive.
Some metadata of the original resources should be copyed in the derived product, and other will be dedicated to the derived product.

- Authors: the full authors (creators and contributors) list should be replicated in the derived metadata. The list can be completed with contributors involved in the derived product curation.
- Dates: the creation and the modification dates are the dates of the DataCenter that provide the derived product
- Abstract: it is not needed to duplicate the original abstract, but the added curation should be explained
- relations: add link to the original product. 
  You can Cite (relation type ```Cites```) the original resource that you can complete with a relation explaining the relationship between the original and the derived product.

  Please : refer to the DataCite ```relationType``` vocabulary and do not extrapolate the semantic.

  Example: **TODO**


example:
```
"relatedIdentifiers": [
    {
      "relationType": "IsVariantFormOf",
      "relatedIdentifier": "10.5270/esa-qa4lep3",
      "relatedIdentifierType": "DOI"
    },
    {
      "relationType": "Cites",
      "relatedIdentifier": "10.5270/esa-qa4lep3",
      "relatedIdentifierType": "DOI"
    }
  ]
```

