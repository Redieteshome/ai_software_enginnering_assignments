## What was the bug?

The `HttpClient` only tried to refresh the token if it was either `null` or an expired `OAuth2Token`. It did not handle cases where the token was a plain object that was not actually an `OAuth2Token` instance. As a result, the Authorization header was not set properly in those cases.

## Why did it happen?

The original refresh logic checked whether the token existed and whether it was an `OAuth2Token` using `instanceof`. Plain objects are “truthy,” but they are not instances of `OAuth2Token`, so the refresh step was skipped and no token was attached to requests.

## Why does your fix solve it?

The fix updates the condition so that the token is refreshed whenever it is not an `OAuth2Token` instance or if it has expired. This guarantees that only valid, non-expired `OAuth2Token` objects are used, and the Authorization header is correctly set.

## One realistic case / edge case not covered by tests

The tests do not cover a situation where a valid `OAuth2Token` expires between validation and its use in a request basically, a time-based race condition.
