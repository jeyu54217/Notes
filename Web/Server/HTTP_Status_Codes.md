
HTTP Status Codes
  - [Informational - 1xx](#informational---1xx)
  - [Successful - 2xx](#successful---2xx)
  - [Redirection - 3xx](#redirection---3xx)
  - [Client Error - 4xx](#client-error---4xx)
  - [Server Error - 5xx](#server-error---5xx)
  - [References](#references)

# Informational - 1xx
  ```
  HTTP_100_CONTINUE
  HTTP_101_SWITCHING_PROTOCOLS
  HTTP_102_PROCESSING
  HTTP_103_EARLY_HINTS
  ```
# Successful - 2xx
  ```
  HTTP_200_OK
  HTTP_201_CREATED
  HTTP_202_ACCEPTED
  HTTP_203_NON_AUTHORITATIVE_INFORMATION
  HTTP_204_NO_CONTENT
  HTTP_205_RESET_CONTENT
  HTTP_206_PARTIAL_CONTENT
  HTTP_207_MULTI_STATUS
  HTTP_208_ALREADY_REPORTED
  HTTP_226_IM_USED
  ```
# Redirection - 3xx
  ```
  HTTP_300_MULTIPLE_CHOICES
  HTTP_301_MOVED_PERMANENTLY
  HTTP_302_FOUND
  HTTP_303_SEE_OTHER
  HTTP_304_NOT_MODIFIED
  HTTP_305_USE_PROXY
  HTTP_306_RESERVED
  HTTP_307_TEMPORARY_REDIRECT
  HTTP_308_PERMANENT_REDIRECT
  ```
# Client Error - 4xx
  ```
  HTTP_400_BAD_REQUEST
  HTTP_401_UNAUTHORIZED
  HTTP_402_PAYMENT_REQUIRED
  HTTP_403_FORBIDDEN
  HTTP_404_NOT_FOUND
  HTTP_405_METHOD_NOT_ALLOWED
  HTTP_406_NOT_ACCEPTABLE
  HTTP_407_PROXY_AUTHENTICATION_REQUIRED
  HTTP_408_REQUEST_TIMEOUT
  HTTP_409_CONFLICT
  HTTP_410_GONE
  HTTP_411_LENGTH_REQUIRED
  HTTP_412_PRECONDITION_FAILED
  HTTP_413_REQUEST_ENTITY_TOO_LARGE
  HTTP_414_REQUEST_URI_TOO_LONG
  HTTP_415_UNSUPPORTED_MEDIA_TYPE
  HTTP_416_REQUESTED_RANGE_NOT_SATISFIABLE
  HTTP_417_EXPECTATION_FAILED
  HTTP_421_MISDIRECTED_REQUEST
  HTTP_422_UNPROCESSABLE_ENTITY
  HTTP_423_LOCKED
  HTTP_424_FAILED_DEPENDENCY
  HTTP_425_TOO_EARLY
  HTTP_426_UPGRADE_REQUIRED
  HTTP_428_PRECONDITION_REQUIRED
  HTTP_429_TOO_MANY_REQUESTS
  HTTP_431_REQUEST_HEADER_FIELDS_TOO_LARGE
  HTTP_451_UNAVAILABLE_FOR_LEGAL_REASONS
  ```    
# Server Error - 5xx
  ```
  HTTP_500_INTERNAL_SERVER_ERROR
  HTTP_501_NOT_IMPLEMENTED
  HTTP_502_BAD_GATEWAY
  HTTP_503_SERVICE_UNAVAILABLE
  HTTP_504_GATEWAY_TIMEOUT
  HTTP_505_HTTP_VERSION_NOT_SUPPORTED
  HTTP_506_VARIANT_ALSO_NEGOTIATES
  HTTP_507_INSUFFICIENT_STORAGE
  HTTP_508_LOOP_DETECTED
  HTTP_509_BANDWIDTH_LIMIT_EXCEEDED
  HTTP_510_NOT_EXTENDED
  HTTP_511_NETWORK_AUTHENTICATION_REQUIRED
  ```

# References
- [RFC 2616](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) 
- [RFC 6585](https://tools.ietf.org/html/rfc6585)
- [RFC 4918](https://tools.ietf.org/html/rfc4918)
- [DRF Status Codes](https://www.django-rest-framework.org/api-guide/status-codes/)
