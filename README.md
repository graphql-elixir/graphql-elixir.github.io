# GrapQL Elixir Docs

GraphQL Elixir docs are powered by [gatsby](https://github.com/gatsbyjs/gatsby).


## Installation

For running locally this docs. You have to execute
```bash
npm install -g gatsby && npm install
```

And then

```bash
gatsby develop
```

## Build

For building the docs into the `public` dir, just run:

```bash
npm deploy
```

## Deploying to the web

This repo is setup as an organisation github pages repo. This means the source material is in the `source` branch and the website is updated from `master`.

To publish manually you need to run the following:

```bash
# generate html from source files and
git checkout source
npm deploy
git add .
git commit -m"Deploy"

# pull the build dir from the source branch into master branch
git checkout master
git checkout source build

# copy to root dir
cp -vR public/* .

# delete public dir
rm -rf public

# commit and pushing to master will deploy
git add .
git commit -m"Deploy latest"
git push
```

Bit convoluted but will automate.

## Automation

Might automate this in a similar fashion to:

https://github.com/graphql-python/graphene/blob/master/.travis.yml#L39-L58

## Thanks

Thanks to the [Graphene Python](https://github.com/graphql-python/graphene/tree/master/docs) team for their great looking site on which this is heavily based.
