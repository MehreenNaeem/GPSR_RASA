# GPSR_RASA

### Data formate
https://rasa.com/docs/rasa/training-data-format/

### For GPSR challange:New vocabulary
you can add data by making changes in data/nlu.yml and domain.yml

#### new plans
add intent: (title of the plan) in data/nlu.yml and also update the domain.yml with new intent. Then add some examples.
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

```[object category]{"entity": "object category"}```
Here "object category" is the title of the entities where [object category] is an element belongs to following entites. In order to avoid data biasing, lookup table is used to specify the elements of the entities (Avoid to enter direct element in entity examples). e.g to add elements in "object category" its lookup table is defined as:
```
- lookup: object category
  examples: |
    - cutlery
    - drinks
    - fruits
```
Make sure to uppgrade the list of intents and entities in domain.yml when you enter new intent or entity in nlu.yml.

### training
train the model after making changes in files. go into the rasa directory where files are defined and train the model
```
rasa train
```
### testing
In python 
```
import json
import requests
    def rasa_response(text):
        req = {"text": text}
        r = requests.post("http://localhost:5005/model/parse", data=bytes(json.dumps(req), "utf-8"))
        response = json.loads(r.text)
        print(response)
        return response
rasa_response('hi')
```
