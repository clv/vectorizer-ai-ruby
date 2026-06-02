# VectorizerAI::AccountApi

All URIs are relative to *https://api.vectorizer.ai/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_account_status**](AccountApi.md#get_account_status) | **GET** /account | Get account status |


## get_account_status

> <AccountStatusResponse> get_account_status

Get account status

Fetch the subscription state and remaining API credits for the authenticated account.

### Examples

```ruby
require 'time'
require 'vectorizer_ai'
# setup authorization
VectorizerAI.configure do |config|
  # Configure HTTP basic authorization: basicAuth
  config.username = 'YOUR USERNAME'
  config.password = 'YOUR PASSWORD'
end

api_instance = VectorizerAI::AccountApi.new

begin
  # Get account status
  result = api_instance.get_account_status
  p result
rescue VectorizerAI::ApiError => e
  puts "Error when calling AccountApi->get_account_status: #{e}"
end
```

#### Using the get_account_status_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AccountStatusResponse>, Integer, Hash)> get_account_status_with_http_info

```ruby
begin
  # Get account status
  data, status_code, headers = api_instance.get_account_status_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AccountStatusResponse>
rescue VectorizerAI::ApiError => e
  puts "Error when calling AccountApi->get_account_status_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**AccountStatusResponse**](AccountStatusResponse.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

