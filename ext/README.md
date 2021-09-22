# Extensions

The basis of the Extension API is described in a document which should be emulated for all extensions.

## Table of Contents

<!-- toc -->
* [Table](#table)
* [Name](#name)
* [Filename](#filename)
* [Detail](#detail)
* [Prior Art](#prior-art)
<!-- /toc -->

## Table

_notice_: All new `./ext/ext-$name.md` docs MUST be added to this table.

| `$name`  | Summary                                              |
|:------------------------:|:----------------------------------------------------:|
| [ext](./ext.md)          | Extensions discovering extensions on registry server |

## Name

Extension names MUST be unique.
Names MAY include a version as part after the extension name. Recommendation is to avoid version 
and use `mediaType` directly to ensure behaviour change when possible.

Each extension's endpoints will be nested below its name similar to the
base extension accessible under a repository.

```HTTP
    GET /v2/{name}/_ext/
```

## Filename

Extention definitions SHOULD be placed under `./ext/`. Extension files 
should follow the `ext-$name.md`. Refer [ext.md](./ext.md) for more details.  

## Detail

Extensions details should describe more endpoints and API that it MAY support and 
also call out error codes encountered via the API are enumerated as in the 
in the following table:

| Code                | Message              | Description                                                                                                                                                                                            |
|---------------------|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `EXTENSION_UNKNOWN` | Extension is unknown | This error MAY be returned when a extension is unknown to the registry in a specified repository. This can be returned with a standard get or if a manifest references an unknown layer during upload. |

## Prior Art

When considering the proposal structure for these extensions, the following processes were considered:

* [Python PEP](https://www.python.org/dev/peps/)
* [Kubernetes KEP](https://github.com/kubernetes/enhancements/tree/master/keps)
