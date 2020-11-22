### Basic checks:
  1. Health check on service itself
  2. Response code 200 with minimum request defined, values/params matching requirements expectation
  3. Response !=200 ( 403, 500, etc) in error cases. E.g. simulation of network error ( service is down, etc)
  4. Schema check for response object itself, to ensure your response structure satisfies bare minimum of your contract:
      1. Json/xml schema check
      2. attributes present as defined in API contract
      3. attribute types as expected
### Request parameters check:
  1. Headers check
  2. Request body check
      1. Ensure your request goes through when request params and values adhere requirements, as defined in contract
      2. Negative validation to ensure request fails when request params and values do not math requirements, e.g:
      3. missing headers
      4. invalid value
      5. invalid type, e.g. timestamp, integer, etc
      6. extra parameter or header in the request itself
      7. boundary check on values itself, e.g. pass values of request params greater than expected for this attribute per contract
### Response parameters check:
  1. Positive test cases on response object itself to satisfy and verify API business logic per contract
      1. Required attributes != nulls, empty, etc
      2.  Values check for core business logic for attributes itself, e.g.
          * Identified set of attributes present in the response and != null, empty, etc per business logic
          * Identified set of attributes returns respective values as expected per contract
      3. Combinations of 1+ variations of business logic for attributes to ensure values match expectations.
  2. Negative test cases on response object itself:
      1. For invalid request to ensure errors are handled appropriately
          * Missing required attributes in the request
          * Invalid/null values for required attributes
          * Invalid/null values for optional attributes
