# Nitric Template Store

Official respository store for Nitric

## Registering your respository
If you would like your repository registered for the central nitric store, raise a pull request with the addition to the repositories manifest.

## Creating a Nitric Template repository
A Nitric respository simply consists of a manifest file in it's root that describes its contents, for example:

repository.yaml
```yaml
name: my-repo-name

templates:
  - name: my-first-template
    lang: javascript
    location: templates/my-first-template
  - name: my-second-template
    lang: python
    location: templates/my-second-template
```

## Creating a Nitric Template

A Nitric template will typically typically consist of the following:
```
function/
Dockerfile
```

Where the function directory is this case contains base userland code. And the dockerfile describes how to build the Nitric application, as a container image. Other supporting files can be added as required depending on the language/runtime you're looking to support e.g. package.json for a node project.