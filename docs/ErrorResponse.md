# VectorizerAI::ErrorResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **error** | [**ErrorResponseError**](ErrorResponseError.md) |  |  |
| **data_received** | **Hash&lt;String, Object&gt;** | Echo of the submitted request data when available. File uploads are summarized instead of echoed. |  |

## Example

```ruby
require 'vectorizer_ai'

instance = VectorizerAI::ErrorResponse.new(
  error: null,
  data_received: null
)
```

