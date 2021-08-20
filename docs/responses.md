# Errors

Error responses from the api will have:

* `status` - Will always be 'failure'
* `code` - An error code in UPPER_SNAKE_CASE. Use this code to check for specific errors.
* `reason` - A debug message meant for developers
* `friendlyReason` - An end-user friendly error message that can be displayed

For example:

```
{
	status: 'failure',
	code: 'CODE_TAKEN',
	reason: 'The code is already taken.  Use a different code.',
	friendlyReason: 'Sorry, that code is already taken. Try a different code.'
}
```

## HTTP Codes

* `200` - Success
* `400` - Bad request. Generally this is poorly formatted data. Check your parameters and read the `code` and `reason` in the error response.
* `403` - Not Authorized. Check the organization/team/etc, that your app has access to it, and that you've properly set your api key.
* `404` - The item that was requested couldn't be found.
* `406` - Generally missing or invalid parameters
* `410` - Deprecated endpoint
* `418` - [I'm a teapot](https://datatracker.ietf.org/doc/html/rfc2324#section-2.3.2)
* `420/429` - You've been rate-limited. Enhance your calm
* `500` - Catch-all error. Check the format of your parameters / request.