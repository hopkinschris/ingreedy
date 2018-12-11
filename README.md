# Ingreedy

#### Natural language processing library for recipe ingredients.

## Usage

```ruby
result = Ingreedy.parse('1 lb. potatoes')
print result.amount
  #=> 1.0
print result.unit
  #=> :pound
print result.ingredient
  #=> "potatoes"
```

### I18n and Custom Dictionaries

```ruby
Ingreedy.dictionaries[:fr] = {
  units: { dash: ['pincée'] },
  numbers: { 'une' => 1 },
  prepositions: ['de']
}

Ingreedy.locale = :fr # Also automatically follows I18n.locale if available

result = Ingreedy.parse('une pincée de sucre')
print result.amount
  #=> 1.0
print result.unit
  #=> :dash
print result.ingredient
  #=> "sucre"
```

### Handling Amounts

By default, Ingreedy will convert all amounts to a rational number:

```ruby
result = Ingreedy.parse("1 1/2 cups flour")
print result.amount
  #=> 3/2
```

However, setting `Ingreedy.preverse_amounts = true`, will allow amounts
to be detected and returned as originally input:

```ruby
Ingreedy.preserve_amounts = true

result = Ingreedy.parse("1 1/2 cups flour")
print result.amount
  #=> 1 1/2
```

## Development

Run the tests:

```
rspec spec
```
