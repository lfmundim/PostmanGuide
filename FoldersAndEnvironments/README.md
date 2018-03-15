[Go back](../README.md)
# Folders/Collections
To create a new *Collection*, click on the **New** button on the top left corner and select **Collection**

![alt-text](../IMG/NEW.PNG?raw=true)
![alt-text](../IMG/CollectionEnvironments.PNG?raw=true)

You will be greeted with the view to create a new collection. In it you can start documenting your API by using [Markdown (.md)](https://guides.github.com/features/mastering-markdown/) inside the *Description* box.

![alt-text](../IMG/CreateNewCollect.PNG?raw=true)

Set your Collection name, start your doc (or not). You can ignore the other tabs for now. Click **Create**.

After creating your first Collection, you should create its *Environment*. Environments are an relative-configuration manager where you can set variables to use any time you want. Usually you would like to create at least one environment for each collection and name it accordingly, to keep things nice and tidy.

I'm going to use Steam's API as an example:

![alt-text](../IMG/NewEnvironment.PNG?raw=true)

Notice I set two variables: *key* and *baseUrl*. Those will be accessible using `{{thisSnippet}}` any time you want, as long as its Environment is selected:

![alt-text](../IMG/SelectEnvironment.PNG?raw=true)

That's a lot for configuring your workspace, [let us use it now.](../Requests/README.md)