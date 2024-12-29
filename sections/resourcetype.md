# Choosing a type for resources
The Resource type is driven by a  ```ResourceTypeGeneral``` which use a controlled vocabulary, completed with a ```ResourceType``` which is a free text.

Examples: Choosing the good Resource type is leaded to the Data publisher.
the following list is indicative only and does not constitute a rule of good practice:

|              | RetourceTypeGeneral | ResourceType     |
|--------------|---------------------|------------------|
|table         | Dataset             | Dataset          |
|spectrum      | Dataset             | Spectrum         |
|image         | Image               | Image            |
|logs of observations | Dataset      | Evolving Dataset |
|Collection    | Collection          | Collection       |
|Service VO    | Service             | IVOA Service     |
|service Web   | Service             | Web Service      |
|knowledgebase | Dataset             | Evolving Dataset |   


Example:

```
"types": {
    "resourceType": "evolving Dataset",
    "resourceTypeGeneral": "Dataset"
  },
"titles": [
    {
      "lang": "en",
      "title": "The Gemini Observation Log (evolving Dataset)"
    }
  ],
```
