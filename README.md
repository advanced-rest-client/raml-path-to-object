
`<raml-path-to-object>`
Helper element that converts selected path to a RAML definition object.


### Example
```
<raml-path-selector raml="[[raml]]" selected-path="{{selectedPath}}"></raml-path-selector>
<raml-path-to-object
  raml="[[raml]]"
  selected-path="{{selectedPath}}"
  selected-object="{{selectedObject}}"
  is-selected-method="{{isSelectedMethod}}"
  is-selected-resource="{{isSelectedResource}}"
  is-selected-documentation="{{isSelectedDocumentation}}"></raml-path-to-object>
```

