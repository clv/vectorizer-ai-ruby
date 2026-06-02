# VectorizerAI::AccountStatusResponse

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **subscription_plan** | **String** | The subscription plan currently associated with the account, or &#39;none&#39;. |  |
| **subscription_state** | **String** | The current subscription state: &#39;active&#39;, &#39;pastDue&#39;, or &#39;ended&#39;. |  |
| **credits** | **Float** | The number of API credits left. Can be fractional, so parse as a double-precision number. |  |

## Example

```ruby
require 'vectorizer_ai'

instance = VectorizerAI::AccountStatusResponse.new(
  subscription_plan: null,
  subscription_state: null,
  credits: null
)
```

