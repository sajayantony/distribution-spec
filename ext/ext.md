# ext-0 -- Index of Distribution Extensions

## Table of Contents

<!-- toc -->
* [Summary](#summary)
* [Reference Explanation](#reference-explanation)
* [Extension Property Descriptions](#extension-property-descriptions)
<!-- /toc -->

## Summary

This base extension is to return the array of names of the extensions.

## Reference Explanation

The base extension may be queries through a `GET` to discover available 
extensions under a repository.

```HTTP
    GET /v2/{name}/_ext/
```

The base extension returns an array of supported extensions with details of the
endpoints as shown below.

```json
{
    "extensions" : [
        {
            "name" : "foo",
            "endpoint" : "_foo"
        }
    ]
}
```

### *Extensions* Property Descriptions

- **`extensions`** *array of objects*

    This REQUIRED property contains a list of supported extensions.

    Each object in `extensions` includes a set extension properties with the
    following additional properties and restrictions.

    - **`name`**  string

        The name of the supported extension.

   - **`endpoint`**  string

        The [relative URI]((https://datatracker.ietf.org/doc/html/rfc1808))
        which can be constructed by replacing 
        the base extension,`_ext` . For e.g. `/v2/{name}/_foo/` would be the
        base URI for operations. 

## Error Codes

Registry implementations MAY chose to not support any extension and the base
extension MAY return the following error message.

| Code                | Message              | Description                                                                                                                                 |
|---------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| `EXTENSION_UNKNOWN` | Extension is unknown | This error MAY be returned when a extension is unknown to the registry in a specified repository. This can be returned with a standard get. |