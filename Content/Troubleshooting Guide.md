## 400
- **Check the environment variable** - **'X-GitHub-Api-Version'** in .env. Be sure that the version exists.   [Check supported API versions](https://docs.github.com/en/rest/about-the-rest-api/?apiVersion=2022-11-28#supported-api-versions)
## 401
- **Check the environment variable** - 'GITHUB-TOKEN' in .env. Be sure that the token is valid. [Visit creating a fine-grained personal access token and go to first four steps](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)

## 403
- **Check the environment variable** - 'GITHUB-TOKEN' in .env. Be sure that the token is valid. [Visit creating a fine-grained personal access token and go to first four steps](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)
- Check requirement permissions for endpoint
- Check rate limits:
	- `x-ratelimit-remaining` header will be `0` - you should wait until x-ratelimit-reset and retry after [[Error handling#Primary rate limit|Error handling primary rate limit]]
	- `retry-after` response header is present, you should not retry your request until after that many seconds has elapsed [[Error handling#Secondary rate limit|Error handling secondary rate limit]]
	[Check best practice](https://docs.github.com/en/rest/using-the-rest-api/best-practices-for-using-the-rest-api?apiVersion=2022-11-28#handle-rate-limit-errors-appropriately) [Status of primary rate limit](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api?apiVersion=2022-11-28#calculating-points-for-the-secondary-rate-limit:~:text=not%20shared%20publicly.-,Checking%20the%20status%20of%20your%20rate%20limit,-You%20can%20use) 
	
## 404
- **Check the environment variable** - 'GITHUB-TOKEN' in .env. Be sure that the token is valid. [Visit creating a fine-grained personal access token and go to first four steps](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token)
- Check requirement permissions for endpoint
## 429
- Check rate limits:
	- `x-ratelimit-remaining` header will be `0` - you should wait until x-ratelimit-reset and retry after [[Error handling#Primary rate limit|Error handling primary rate limit]]
	- `retry-after` response header is present, you should not retry your request until after that many seconds has elapsed. [[Error handling#Secondary rate limit|Error handling secondary rate limit]]
	[Check best practice](https://docs.github.com/en/rest/using-the-rest-api/best-practices-for-using-the-rest-api?apiVersion=2022-11-28#handle-rate-limit-errors-appropriately)[Status of primary rate limit](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api?apiVersion=2022-11-28#calculating-points-for-the-secondary-rate-limit:~:text=not%20shared%20publicly.-,Checking%20the%20status%20of%20your%20rate%20limit,-You%20can%20use) 
## Validation failed
- If you receive the 'Validation failed' massage you should check the length of your searching query. It should be less then 256. [Check the limitation](### [Limitations on query length](https://docs.github.com/en/rest/search/search?apiVersion=2022-11-28#limitations-on-query-length))  [[Error handling#Limitation on query length|Error handling limitation query length]]

