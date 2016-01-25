---
title: Basic Types
description: Walkthrough Basic Types
---

# Basic Types

GraphQL Elixir define the following base Scalar Types:
- `GraphQL.Type.String`
- `GraphQL.Type.Int`
- `GraphQL.Type.Float`
- `GraphQL.Type.Boolean`
- `GraphQL.Type.ID`

Also the following Types are available:
- `GraphQL.Type.List`
- `GraphQL.Type.NonNull`
- `GraphQL.Type.JSON`

## Shortcuts

There are some shortcuts for simplifying your schema.

```elixir
# A list of strings
string_list = graphene.List(graphene.String())
string_list = graphene.String().List

# A non-null string
string_non_null = graphene.String().NonNull
string_non_null = graphene.NonNull(graphene.String())
```


## Custom scalars

You can also create a custom scalar for your schema.
Add a custom Scalar Type as follows:

```elixir
defmodule GraphQL.Type.CustomType do
  defstruct name: "CustomType", description:
    """
    CustomType description
    """

  def coerce(value), do: <...>
end

defimpl GraphQL.Types, for: GraphQL.Type.CustomType do
  def parse_value(_, value), do: <...>
  def serialize(_, value), do: <...>
end```
