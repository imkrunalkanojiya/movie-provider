# Movies Provider

```
import { Fetcher, makeSimpleProxyFetcher, makeProviders, makeStandardFetcher, targets} from "movies-provider";
```

## Fetcher

`Fetcher` is a type that represents a function that makes a request to a URL and returns a response. It's a generic term for a function that "fetches" data from a URL. In this code, a Fetcher function takes two parameter

- `a`: likely the URL to fetch
- `b`: likely options for the fetch request (e.g., headers, method, body)

The Fetcher function returns a response, which is an object with properties like **body, finalUrl, statusCode, and headers**

## makeSimpleProxyFetcher

`makeSimpleProxyFetcher` is a function that creates a new `Fetcher` function. It takes two parameters:

- `proxyUrl`: the URL of a proxy server
- `fetchFunction`: a Fetcher function to use for making the actual request

The `makeSimpleProxyFetcher` function returns a new Fetcher function that:

- Uses the provided `proxyUrl` to make the request
- Uses the provided `fetchFunction` to make the actual request to the proxy URL
- Returns the response from the `proxy URL`

In essence, `makeSimpleProxyFetcher` creates a `Fetcher` function that acts as a proxy between the caller and the actual request. This allows for load balancing, caching, or other proxy-related functionality to be added to the request process.

`makeSimpleProxyFetcher` is used to create a load-balanced proxy fetcher, which randomly selects a proxy URL from a list and uses it to make the request.


## makeProviders

`makeProviders` is a function that creates a `Providers` object, which is a collection of functions for making requests to a specific target (e.g., browser, extension). It takes an options object with the following properties:

- `fetcher`: a Fetcher function for making requests
- `target`: the target of the requests (e.g., targets.BROWSER or targets.BROWSER_EXTENSION)
- `proxiedFetcher`: an optional Fetcher function for making proxied requests
- `consistentIpForRequests`: a boolean indicating whether to use a consistent IP address for requests

## makeStandardFetcher

`makeStandardFetcher` is a function that creates a `Fetcher` function using the provided `fetch` function (e.g., the native browser `fetch` function). This `Fetcher` function makes standard requests to the target.

## targets

`targets` is an object with properties representing different targets for requests, such as:

- `targets.BROWSER`: the browser itself
- `targets.BROWSER_EXTENSION`: a browser extension

These targets determine how requests are made and which `Fetcher` function is used.

`getProviders` returns a `Providers` object based on whether the extension is active or not. If the extension is active, it uses `makeExtensionFetcher` as the `fetcher`. Otherwise, it uses `makeStandardFetcher` as the `fetcher` and `makeLoadBalancedSimpleProxyFetcher` as the `proxiedFetcher`.

I know description was not intresting as per you think 😅. But this is what it is.

## Support

<a href="https://www.buymeacoffee.com/krunalkanojiya" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>
