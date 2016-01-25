---
title: Getting Started
description: A Quick guide to GraphQL Elixir
---

# Getting started

Let's build a basic GraphQL schema from scratch.


## Requirements

- Elixir (1.1+)


## Installation

First, add GraphQL to your `mix.exs` dependencies:

```elixir
defp deps do
  [{:graphql, "~> 0.1.1"}]
end
```

Add GraphQL to your `mix.exs` applications:

```elixir
def application do
  # Add the application to your list of applications.
  # This will ensure that it will be included in a release.
  [applications: [:logger, :graphql]]
end
```

Then, update your dependencies:

```sh-session
$ mix deps.get
```

## Usage

First setup your schema

```elixir
defmodule TestSchema do
  def schema do
    %GraphQL.Schema{
      query: %GraphQL.Type.ObjectType{
        name: "RootQueryType",
        fields: %{
          greeting: %{
            type: %GraphQL.Type.String{},
            resolve: {TestSchema, :greeting}
          }
        }
      }
    }
  end

  def greeting(_, %{name: name}, _), do: "Hello, #{name}!"
  def greeting(_, _, _), do: "Hello, world!"
end
```

Execute a simple GraphQL query

```elixir
iex> GraphQL.execute(TestSchema.schema, "{greeting}")
{:ok, %{greeting: "Hello, world!"}}
```
