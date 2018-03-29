**Why do you think different cache times for the nginx cache and for the browser were defined?**

There are different levels of cache. Browser cache helps improve performance by letting browser to cache elements that not change frequently. For example a company logos image. Server or proxy cache are a way to cache elements and respond with the same results to every query and user.

Browser cache is for individual users. 
Reverse proxy cache is unique.
You can control the cache with the reverse proxy, for instance 1 minute.
If the browser cache is bypassing the cache-control age, you still have the proxy cache configuration, in this case 1 min.
