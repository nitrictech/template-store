# Nitric Template Store

The Nitric Template Store is a central index of Nitric Template Repositories consisting of various Function and Service templates. These templates provide scaffold, build and runtime support for numerous service runtimes and languages.

The Nitric CLI uses the template store to locate and install template repositories for use in Nitric projects.

> Currently, only official repositories are tracked in the template store. Community and Private repositories will be supported in future.

## Registering your respository
If you would like your repository registered in the central nitric store, raise a pull request with the addition to the repositories manifest. Your request will be reviewed and feedback will be provided or the request will be approved by a member of the Nitric team.

## Creating a repository
A Nitric respository consists of a manifest file in it's root that describes its contents, for example:

__repository.yaml__

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

__*Repository:*__

| Property    | Description                                                               |
| ----------- | ------------------------------------------------------------------------- |
| `name`      | Governs how your repository will be listed in CLI and UI repository lists |
| `templates` | Array of template objects containing the properties of each template      |

__*Template:*__

| Property   | Description                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------- |
| `name`     | The name of the template, displayed in the CLI and how it will be referenced in a Nitric.yaml file. |
| `lang`     | The language of the runtime. Currently unused, may be deprecated in future.                         |
| `location` | The relative path to the template directory within the repository                                   |

## Creating a template

At minimum a Nitric template typically consists of:

```
function/
Dockerfile
```

The `function` directory contains a function scaffold, which will be copied into a project when a new function is created from the template. When building a function (in a project) the user defined function code will replace the contents of this folder prior to building the contain image.

The `Dockerfile` describes how to build the Nitric function/service into a container image. This file will typically include the Nitric Membrane binary, runtime/language specific build tools, build steps and invocation settings.

Along with these two files, any other supporting files can be added as required depending on the language/runtime you're looking to support e.g. package.json for a node.js project.