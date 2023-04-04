# JSON Schema

_A representation of a person, company, organization, or place_

## Properties

- **`fruits`** _(array)_
  - **Items** _(string)_
- **`vegetables`** _(array)_
  - **Items**: Refer to _#/definitions/veggie_.

## Definitions

- **`veggie`** _(object)_

  - **`veggieName`** _(string)_: The name of the vegetable.
  - **`veggieLike`** _(boolean)_: Do I like this vegetable?

  Examples:

  ```json
  {
    "veggieName": "carrot",
    "veggieLike": true
  }
  ```

## Examples

```json
{
  "fruits": ["apple", "orange"],
  "vegetables": [
    {
      "veggieName": "cabbage",
      "veggieLike": true
    }
  ]
}
```
