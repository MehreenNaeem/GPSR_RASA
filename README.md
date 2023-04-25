# GPSR_RASA

### Data formate
https://rasa.com/docs/rasa/training-data-format/

### For GPSR challange how to add words
you can add data by making changes in data/nlu.yml and domain.yml

#### new plans
add intent: (title of the plan) in data/nlu.yml and also the update the domain.yml with new intent. Then add some examples.
Try to add synonyms of the word first without enttites and then make examples using entities (To avoid data biasing)

```
- intent: search
  examples: |
    - find
    - search
    - find the [colour]{"entity": "colours"} [object]{"entity": "object"} in the [rm]{"entity": "room"}
    - search for the[person]{"entity": "person"} [gesture]{"entity": "gestures"} her hand at the [location]{"entity": "location"}
```
#### new entities
you can specify new entities by making examples in the intent data/nlu.yml. 
[object category]{"entity": "object category"}
here "object category" is the title of the entities where [object category]


