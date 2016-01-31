---
title: ObjectTypes
description: Walkthrough ObjectTypes
---

# ObjectTypes

An ObjectType is the single, definitive source of information about your data.
It contains the essential fields and behaviors of the data you’re querying.

## Quick example

Lets make a `Person` ObjectType which can be represented as a GraphQL type:

```graphql
type Person {
  id: ID
  firstName: String
  lastName: String
}
```

In Elixir this would be written like this:

```elixir
%ObjectType{
  name: "Person",
  description: "A Person",
  fields: %{
    id: %{type: %ID{}},
    firstName: %{type: %String{}},
    lastName: %{type: %String{}}
  }
}
```

**id**, **first_name** and **last_name** are the fields of the ObjectType.

The description is optional, but is useful for documenting your schema and is used by tools like GraphiQL.
