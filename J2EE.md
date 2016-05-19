##1. Difference between forward and redirect

|----|-----|
|Forward|1. a forward is performed internally by the servlet
2. the browser is completely unaware that it has taken place, so its original URL remains intact
3. any browser reload of the resulting page will simple repeat the original request, with the original URL
Redirect|
|redirect| is a two step process, where the web application instructs the browser to fetch a second URL, which differs from the original
a browser reload of the second URL will not repeat the original request, but will rather fetch the second URL
redirect is marginally slower than a forward, since it requires two browser requests, not one
objects placed in the original request scope are not available to the second request|

