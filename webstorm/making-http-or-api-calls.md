# Making HTTP or API Calls in Webstorm

I was reaching for postman and didn't want to bother looking up my login for that.
Honestly, I was also annoyed I even needed a login to make some simple API calls.
I looked for Postman alternatives and found [a page showing how to make HTTP calls in IntelliJ](https://lp.jetbrains.com/intellij-idea-http-client)
and since [WebStorm](https://www.jetbrains.com/webstorm/) is also a JetBrains product I figured I must have access to this feature as well.
And I do! It's a plugin called [HTTP Client](https://www.jetbrains.com/help/webstorm/http-client-in-product-code-editor.html) and it's installed by default in WebStorm.

So I looked it up in Settings -> Plugins and then saw that it mentioned creating `.http` or `.rest` files.
Once you create those, you can define specific API calls in them, and then click a handy little play button and WebStorm will run the request for you and provide the response in the `Services` panel.

Here's an example of a `.rest` file:

```http
### Increment count
PATCH http://localhost:8080/api/count
Content-Type: application/json

{
  "incrementBy": 1
}
```

It's a pretty straightforward format; just an HTTP request.
This makes testing endpoints I'm working on in Express even easier since I don't even have to leave the IDE.