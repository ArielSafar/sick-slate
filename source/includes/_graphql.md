
# GraphQL
ה-API של הישויות של Sick מתחלק לשניים - בעבור שליפות קיים API GraphQL, ובעבור יצירה, עדכון ומחיקה קיים REST API.

<aside class="notice">יש לשלוח בכל בקשה את ה-API Key שלכם! פרטים נוספים בחלק "אותנטיקציה"</aside>

## סכמת Entities

```python
import kittn

api = kittn.authorize('buttowski')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: buttowski"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('buttowski');
let kittens = api.kittens.get();
```

```typescript
import kitten from 'kittn';

let api = kitten.authorize('buttowski');
let kittens = api.kittens.get();
```

```graphql
query {
  entities(id: { _match: [""] } povId: { _match: [""] }) {
    id
    title
    povId
    nicknames
  }
}
```

> השאילתה שלמעלה מחזירה JSON בפורמט הבא:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## סכמת Search

```python
import kittn

api = kittn.authorize('buttowski')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: buttowski"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('buttowski');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## סכמת Autocomplete


```python
import kittn

api = kittn.authorize('buttowski')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: buttowski"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('buttowski');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete


