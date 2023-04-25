# Redirects

There is Redirects global where you can define your 301 and 302 redirects. This only kicks in when a 404 error is triggered as all logic is being done in `resources/views/errors/404.antlers.html`.

> Note: by default only `superusers` and the `marketeer` role get access to this feature.

You can also use this feature to make temporariy vanity urls. So you can make `mywebsite.com/promo` redirect to `mywebsite.com/blog/this-is-what-we-have-to-offer`. Make sure you use a 302 status code for this.
