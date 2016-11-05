
`<raml-path-to-object>`
Helper element that converts selected path to a RAML definition object.
It also fill up `selectedObject` with additional properties to match internall data model
so this element must always be used whem displaying documentation using ARC's set of elements.

RAML's JS parser don't add definitions for traits or security schemes to resources or
methods. This element will look for the definition in source RAML and assign this definitions
to the `selectedObject`.

To ilustrate, parser's JSON output for a method would be:
```
{
  "method": "get",
  "is": {
    Paginated: {
      "resourceType": "..."
    }
  },
  "securedBy": [
    "oauth_2_0"
  ]
}
```
But after using this element it would be:
```
{
  "method": "get",
  "is": [{
    "name": "Paginated",
    "description": "...",
    ...
  }],
  "securedBy": [{
    "describedBy": {...},
    "settings": {...},
    "name": "oauth_2_0"
  }]
}
```

Full list of affected properties:
- is - replaced IDs with object definition
- securedBy - replaced IDs with object definition
- queryParameters - computed all possible params from all parent resources, traits ans security schemas
- headers - computed all possible headers from all parent resources, traits ans security schemas
- uriParameters - computed all possible params from all parent resources, traits ans security schemas
- responses - computed all possible responses from all parent resources, traits ans security schemas
- fullUrl - a full URL for given resource / method

### Usage
```
<raml-path-selector raml="[[raml]]" selected-path="{{selectedPath}}"></raml-path-selector>
<raml-path-to-object
  raml="[[raml]]"
  selected-path="{{selectedPath}}"
  selected-object="{{selectedObject}}"
  is-method="{{isMethod}}"
  is-resource="{{isResource}}"
  is-documentation="{{isDocumentation}}"></raml-path-to-object>
```

