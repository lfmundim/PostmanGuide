[Go back](../README.md)
# Using Request Responses as Variables
So you just created your first request, it worked ✨brilliantly✨ but you needed part of the response on another request as a parameter. Even though you can easily copy and paste it, **it's not really *optimal***. Let's learn about one of *Postman's* nifty features: **scripts**.

Go to your first request, the one with the response you need, and click on the *Tests* tab. This tab is *usually* for testing the request, but what it does is really simple: it runs a JS **after** the request is done. That means you can use basically **anything** present in the default JS library PLUS *Postman's* own methods, including *saving environment variables on the fly*!

In sum, this is the script you are looking for:
```Javascript
var jsonData = JSON.parse(responseBody);
postman.setEnvironmentVariable("steamId", jsonData.response.steamid);
```
![alt-text](../IMG/SavingResponseTests.PNG?raw=true)

What it does is it parses the API's response's Body into a JSON and saves the given field (in this case, `response.steamid`) into the Environment Variable `{{steamId}}`. If there is no such variable, it will create one either way! Now you can access it anywhere within the environment!

So, say we have a new request that uses such variable: 

```
{{baseUrl}}/GetPlayerSummaries/v0002/?key={{key}}&steamids=##########
```

all you gotta do is put the new variable in place:

```
{{baseUrl}}/GetPlayerSummaries/v0002/?key={{key}}&steamids={{steamId}}
```

and as long as you have run the previous request beforehand, the new request should work perfectly!

But... that still doesn't look optimal! Yup! There is an even better way:

# Chaining Requests
Postman has a *very* useful feature: the **Pre-request scripts**. It works the very same way as the *Test scripts*, meaning you can set a JS to run another API Request before running the current one, *and save the first one's response to use as a variable!*

Click on the *Pre-request scripts* tab and you will have a new code-box to type in. There is a large variety of what you can do in there, but lets stick to the basic: running another request and saving the desired response:

```Javascript
pm.sendRequest({
    url: pm.environment.get("baseUrl") + '/ResolveVanityURL/v0001/?key=' + pm.environment.get("key") + '&vanityurl=lucasfmundim',
    method: 'GET',
    body: {
        mode: 'raw'
    }
}, function (err, res) {
    var jsonData = res.json();
    postman.setEnvironmentVariable("newSteamId", jsonData.response.steamid);
}); 
```

The `pm.environment.get` method gets an environment variable and uses it just like `{{thisDoes}}`, but the second option is not available on JS. You can set and get any number of environment variables using this and use them on the new request just as you would normally:

```
{{baseUrl}}/GetPlayerSummaries/v0002/?key={{key}}&steamids={{newSteamId}}
```

and it should work brilliantly!

![alt-text](../IMG/PreRequestScript.PNG?raw=true)

By the way, you can also set headers on the pre-request script method:

```Javascript
pm.sendRequest({
    url: 'https://postman-echo.com/post',
    method: 'POST',
    header: {
        'headername1:value1'
    },
    body: {
        mode: 'raw',
        raw: JSON.stringify({ key: "this is json" })
    }
}, function (err, res) {
    console.log(res);
});
```