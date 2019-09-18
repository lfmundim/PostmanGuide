[Go back](../README.md)
# Requests
Create a *new request* by clicking on the **New** button again and selecting *Request*. You will be greeted by a new window:

![alt-text](../IMG/NewRequest.PNG?raw=true)

Once again you will have an open box to type in a description in Markdown for the new Request. Fill it up whenever you please, as it will be available for editing any time you want. Set a brief but descriptive request name and select its Collection and click *Save*

You will see now a new Tab set for a **GET** Request. Change it to whatever you need by clicking the drop-down menu.

![alt-text](../IMG/SampleRequest.PNG?raw=true)

Fill in the request with its Url and, if needed, use the *Headers* and *Body* tabs at will. Don't mind the other tabs for now.

Note that you *can* and **should** use your `{{environmentVariables}}` now as it makes it simpler to read by hiding some information, leaving only what you **need** to see.

Click *Send* to test your Request. Your output should be right below.

![alt-text](../IMG/SampleResponse.PNG?raw=true)

If everything is good, click *Save*.

[But... what if you need that API's response on another request?](../ChainingRequests/README.md)