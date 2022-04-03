# Validation

There are many validators that can be applied to a data object,
a validator has a name and one or more properties, properties can be
literal values, or have sub-properties.

### required
Specifies whether is a field is required or not.

- value: true if the field is required.
- message: The message to be displayed if this validation rule fails.

```yml
validation:
  name:
    required:
      value: true
```

### length 
Used to validate the length of a string of text.

- min: The minimum length of a string, inclusive.
  - value: The minimum value.
  - message: The message to be displayed if this validation rule fails.
- max: The maximum length of a string, inclusive.
  - value: The maximum value.
  - message: The message to be displayed if this validation rule fails.

```yml
validation:
  addressLine1:
    length:
      min: 8
      max: 64
```


### min
Specifies a minimum value for a number.

- value: The minimum value.
- message: The message to be displayed if this validation rule fails.

```yml
validation:
  age:
    min:
      value: 18
      message: You must be over 18 to use this product.
```

### max
Specifies a maximum value for a number.

- value: The maximum value.
- message: The message to be displayed if this validation rule fails.

```yml
validation:
  amountSent:
    max:
      value: 1000
      message: You can not send more than £1000 in one transaction.
```

### pattern
Specifies a [Regular Expression](https://github.com/topics/regex) to match this string against.

- value: The regular expression.
- message: The message to be displayed if this validation rule fails.

```yaml
validation:
  domainName:
    pattern:
      value: /(?:www\.)?(\w+)\.(com|net|co\.uk)/i
      message: Must specify a valid domain name.
```
