
Goal: 
1. Store the static files (js, css) for long period of time in cache so that we can serve these files quickly.
2. Always serve the fresh file if the file is updated.

solution:
CDN caches the file according to its url.
1. E-tag: 
filename remains uchanged we track the changes by checking if-not-modified header, that needs to be verified by the server. 
2. Cache busting:
client requests for the updated resourse with new url. CDN does not find it in the cache as the url changes. so it fetches the updated resourse withour relying on cache validation.