# Explanation

## What was the bug?
The client failed to attach the Authorization header when the OAuth2 token was stored as a dictionary. The logic only checked for missing or expired OAuth2Token objects; as a result, dictionary-based tokens bypassed the refresh mechanism entirely, leaving requests unauthenticated.

## Why did it happen?
The request method was designed with the strict assumption that the token would be an OAuth2Token instance. However, the test suite initialized the client using a dictionary. Because the type check was too narrow, the refresh logic never triggered, and no header was generated.

## Why does your fix solve it?
I introduced a condition to detect if the token is a dictionary and trigger a refresh if so. This leverages the existing `refresh_oauth2()` method to cast the dictionary into a formal OAuth2Token object. This ensures the header is correctly populated before the request is executed, satisfying the test requirements with minimal code changes.

## One realistic case / edge case not covered
The fix does not validate the dictionary's internal schema. If a dictionary is passed with missing or malformed keys (for example, a missing `access_token`), the client will raise a KeyError. Adding a full validation layer would have fulfilled the "minimal fix" constraint.
