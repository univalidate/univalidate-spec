# Specification

### Goal
The main goal of Univalidate is to streamline and consolidate validation of data by creating a
schema which can evaluated equivalently in any environment.

### Data Structure
This specification does not mandate any particular structure for the validation schema, however it
does make some recommendations:

- If the end user is going to create the schema manually, use a language like [YAML](https://github.com/yaml/yaml-spec).
- If the data is being transferred over HTTP, use [JSON](https://github.com/topics/json).
- Frameworks can also abstract the creation of the schema.

#### Example

All examples are given in YAML format.

```yaml
validation:
  name:
    required:
      value: true
      message: Name is a required field.
    length:
      min:
        value: 1
        message: Name must be 
      max: 64
      message: Name must be between {min} and {max} characters.
  age:
    min:
      value: 18
      message: You must be {value} or older to use this service.
    max:
      value: 65
      message: You must be {value} or younger to use this service.
```

The above specification would validate a data object with a `name` and `age`. It would
expect that the `age` is at least 18 at most 65. It would also expect that the `name` is
1-64 characters long.

If validation were to fail on any given object, a list of failing properties and reasons would
be returned.

```json
{
  "name": "Joe Bloggs",
  "age": 34
}
```

Would validate successfully, but,

```json
{
  "name": "Anne Bloggs",
  "age": 13
}
```

Should fail with a message akin to:

```json
{
  "validationErrors": {
    "age": "You must be 18 or older to use this service."
  }
}
```

### Format

Put simply, the structure is as follows:

```yaml
validation: (1)
  fieldName: (2)
    validatorName: (3)
      validatorProperty1: (4)
        subProperty: value (5)
      validatorProperty2: (6)
        value: value (7)
```

1. Specifies this is a Univalidate schema.
2. The name of a field on the validated data object.
3. The validator name reference.
4. A property of this specific validator.
5. A sub-property for this specific validator property.
6. A second validator property.
7. The value of the second validator property.

### Shorthand syntax

If a property only has a `value` sub-property, or all of the other sub-properties
are optional, then a shorthand syntax can be used:

```yaml
validation:
  age:
    min: 18
    max: 65
```

### Templating
 
In validation messages, templating can be used for more robust
validation schemas, a template uses the `{curly brace}` syntax. A templated
message can access other properties from its validator.

```yaml
validation:
  name:
    length:
      min: 2
      message: Your name must be longer than {min} characters.
```

In the above example, the validation failure message would be: `Your name must be longer than 2 characters.`

[Next - Validators](./3--validators.md)
