# Error handling

## Authorization
- Script in cell checks that the .env file has all variable. If variable isn't exist or has mistake yoy see the massages like:
`Error - you miss token or version, check .env`
`Authentication failed. Status code: 401`

## Limitation on query length
- for handling that error you have length check. If the length is more then 256 chars you receive the message:
`Too long! Max length — 256. Repeat.`

## Primary rate limit
403 or 429 errors. This limit handling by checking the `X-Ratelimit-Remaining` response's header. If it == 0 you receive the massage like:
`Primary rate limit reached. Waiting for 33 seconds...`
But amount of seconds depend on value of `X-RateLimit-Reset` - after that time plus 1 second the query continues.
## Secondary rate limit
- 403 or 429 errors. This limit handling by checking the 'Retry-After' header in response's headers. If you reach that limit you receive the massage:
 `Secondary rate limit reached. Waiting for 60 seconds...`
 You query continues after 60 second. 
 
