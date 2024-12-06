# Error handling

## Authorization
- Script in cell checks that the .env file has all variables. If a variable doesn't exist or has a mistake you see the messages like:
`Error - you miss token or version, check .env`
`Authentication failed. Status code: 401`

## Limitation on query length
- for handling that error you have a length check. If the length is more than 256 chars you receive the message:
`Too long! Max length — 256. Repeat.`

## Primary rate limit
403 or 429 errors. This limits handling by checking the `X-Ratelimit-Remaining` response's header. If it == 0 you receive the message like:
`Primary rate limit reached. Waiting for 33 seconds...`
But the amount of seconds depends on the value of `X-RateLimit-Reset` - after that time plus 1 second the query continues.
## Secondary rate limit
- 403 or 429 errors. This limits handling by checking the 'Retry-After' header in the response's headers. If you reach that limit you receive the message:
 `Secondary rate limit reached. Waiting for 60 seconds...`
 Your query continues after 60 seconds. 
 
