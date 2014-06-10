# Ruby/JS Web Development Cheatsheet

Here are some useful and sometimes hard-to-remember snippets for completing
common web development tasks.

## Table of Contents

- [Key/Value Syntax](#keyvalue-syntax)
- [JSON](#json)
  - [Ruby](#ruby)
  - [Javascript](#javascript)
- [Query String Parameters](#query-string-parameters)
  - [Ruby](#ruby-1)
  - [Javascript](#javascript-1)

# Key/Value Syntax

| Language   |     What you type      | What it does |
| ---------- | ---------------------- | ------------ |
| Ruby       | `{sauce: "sriracha"}`  | `{:sauce => "sriracha"}` |
| Javascript | `{sauce: "sriracha"}`  | `{"sauce": "sriracha"}`  |

---

# JSON

| Language   | Package  |    From JSON         | To JSON |
| ---------- | -------- | --------------------- | ------- |
| Ruby       | `'json'` | `JSON.parse(raw)`     | `model.to_json()` |
| Javascript | N/A      | `JSON.parse(raw)`     | `JSON.stringify(model)`  |

## Ruby

### FROM JSON String TO Ruby Object

Notice that we lose some information in the transition: the keys used
to be symbols, but now they're strings.

```ruby
require('json') # JSON

beastJSON = '{"name":"Crocotillion","diet":"carnivore","habitat":"swamp"}'
JSON.parse(beastJSON) #=> {"name" => "Crocotillion", "diet" => "carnivore", "habitat" => "swamp"}
```

### FROM Ruby Object TO JSON String

```ruby
require('json') # Object::to_json()

beast = {
  :name => "Crocotillion",
  :diet => "carnivore",
  :habitat => "swamp"
}

beast.to_json() #=> '{"name":"Crocotillion","diet":"carnivore","habitat":"swamp"}"'
```

## Javascript

### FROM JSON String TO Javascript Object

```js
beastJSON = '{"name": "Crocotillion"}';
JSON.parse(beastJSON) //=> {"name": "Crocotillion"}
```

### FROM Javascript Object TO JSON String

```js
beast = {"name": "Crocotillion"};
JSON.stringify(beast); //=> '{"name": "Crocotillion"}'
```

---

# Query String Parameters

| Language   | Package                | From Query String              | To Query String                 |
| ---------- | ---------------------- | ------------------------------ | ------------------------------- |
| Ruby       | `rack/utils`           | `Rack::Utils.parse_query(qs)`  | `Rack::Utils.build_query(data)` |
| Javascript | [jQuery]/[deparam]     | `$.deparam(qs)`                | `$.param(data)`                 |

[jQuery]: http://api.jquery.com/jquery.param/
[deparam]: https://github.com/chrissrogers/jquery-deparam

## Ruby

### FROM Query String TO Ruby Hash

```ruby
require 'rack/utils'
Rack::Utils.parse_query("name=Crocotillion") #=> {"name" => "Crocotillion"}
```

### FROM Ruby Hash TO Query String

```ruby
require 'rack/utils'
Rack::Utils.build_query({"name" => "Crocotillion"}) #=> "name=Crocotillion"
```

## Javascript

### FROM Query String TO Javascript Object

```js
$.deparam("name=Crocotillion"); //=> {"name": "Crocotillion"}
```

### FROM Javascript Object TO Query String

```js
$.param({"name": "Crocotillion"}); //=> "name=Crocotillion"
```
