# A Workshop on Practically Applying Machine Learning to Streaming Data using Watson Studio
### You have data streaming in from sensors. You want to train a model on that data and apply it to the data in real time, in the real world.

## Introduction
The term "Machine Learning" or "AI" is fairly well understood by a lot of people but when it comes to you actually building a machine learning model and applying it to real data, I, for one, had a lot of unanswered questions, for example:

* I know you create these models by training them but what do I train? What is the thing that sits there waiting to be given knowledge?
* What do I end up with after a model has been created and trained? Is it just some code? What does it need to run on?
* Assuming it is some code, what does that look like? How do I call it? What about authentication and management of that "thing"?
* Then there's a whole question about how do you maintain it, change it, if new information comes along that needs to be incorporated eg in the summer it becomes clear that temperature is more or less of a factor that you thought? Or in autumn, who knew leaves falling on something would be a thing?

You can find the solution to all these questions above by experimenting and doing it yourself, with various technologies and techniques, but the value of using a cloud service like Watson Studio really becomes evident in situations like this, I'd suggest. Really shortening the time to implement a working solution and really reducing the learning time that might otherwise be involved.

## Summary
You will create a simple spreadsheet containing data you might get from a sensor. This allows you to get you familiar with how a model is created and you can then use that knowledge when thinking about your real data later. 
You will create a Machine Learning model from the data with no code (using the powerful IBM Auto AI service). We will see how this pretty much performs the complex role of a data scientist for you in most situations.
Critically we will then be able to see what this abstract idea of a Machine Learning model looks like and how it can be practically used (put somewhere where it can run, tested with some manually input data, called from code/your app/system etc).

## Steps
The first thing we need in order to train something, is knowledge or data.
In the real world this might mean a LOT of data. It's the job of a data scientist to prepare and make sense of that data so the correct algorithm (from a finite but large list) can be used to create a model. Finding that best fit of data and algorithm is the art of data science and can be a long and iterative process that may even result a new algorithm being invented or created. It's why data science is such a skilled discipline. However, as with any area, there is a scale of complexity. This is where Watson Studio and the Auto AI feature of Watson Studio comes in. The reality is that for a lot of situations the data science process, although long and iterative, doesn't need the skill of a human, it just needs processing power to run that iterative process and compare results. IBM Auto AI does just that.

Given some data it will perform the basic role of a data scientist for us ... to prepare the data and iteratively run it through a selection of algorithms that it thinks have a good chance of success, compare the results and build a model that we can test, based on those results.

1. I've created a file we can use for this workshop [here](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/sensorData.csv). Essentially the data in this file shows one thing ... once "y deflection" reaches 1.2 we get a failure. Although temperature and x deflection change throughout the file, I've crafted the data so that these should have no baring on the likelihood of failure and we should end up with a model that simply predicts failure as y deflection increases towards 1.2.
2. No we can set up our Data Science environment on IBM Cloud. This is all contained within the [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) service, which you can set up for free (and it will remain available if you use it at least once every 30 days). Create this service and then click the Get Started button.
3. Slightly confusingly, this then opens "IBM Cloud Pak for Data" but don't worry, Watson Studio is integral to Cloud Pak for Data so this is what Watson Studio runs within.
4. Underneath the welcome message you'll see three options. Select **Create a project** link under **Work with data** then click **Create and empty project**
5. Give the project a name. Every project will have files and data associated with it and they need to be stored somewhere. You may be asked to create some Cloud Object Storage at this point. If you are, then follow that process then click Create to create the project. If you already have storage configured this will automatically be selected.
6. You'll then be presented with a page where you can add and manage all the components of the project. One thing to note here is the **Environments** page. This is important beacuse it allows you to track how much of your free credit is left, and if you sign up for the paid service, how much resource it is using.
7. Click on the **Assets** tab and note the **file upload** section on the right had side. Add the data file discussed above to your project.
8. Click on the **Settings** tab and locate the **Associated services** section. For specific tasks, Watson Studio needs a service to do that work. For example, no machine learning is going to to happen or be available to use in your system without a machine learning service being connected to Watson Studio.  Click on the **Add service** drop down on the right hand side and select **Watson**. If you have a **Watson Machine Learning service** already set up on your cloud account you will be able to select it. If not, you can create one here by selecting the **New service** blue button and then add that service.
9. Next click on the **Add to project** blue button and select the **Auto AI Experiment** option. You'll need to give that service a name. Note that this Auto AI Experiment service required the Machine Learning service we just associated with the project. It also has some resource requirements that are quite high (20 capacity units per hour) but we will only be using it for a couple of minutes so it's nothing to worry about in this case. 
10. Now we are ready to get Watson to build our machine learning model automatically via the Auto AI service. This where it does the job of a Data Scientist by crunching the data and trying to fit it to a number of likely algorithms and comparing the result/performance of each to get the best one.
11. Select the **Select from project** button and add the data we imported earlier. Watson will look at the data and ask what particular thing you want to be able to predict using your model that will be created. Select **"failed"** from the list because we want to know how likely failure is based on what we input to the model. Note that you can view the data and look at distribution etc by clicking the slider icon next to the imported data file on the left. Note also that you can fine tune the Auto AI experiment by clicking on the **Experiment settings** button next to the **Run experiment** button. 
12. Click the **Run experiment** button and note the progress being displayed, which can be quite interesting to watch. Try switching the view around and note the "leaderboard".
13. When the experiment is complete, you can view the leaderboard and save the top (or any other) result either as a machine learning model that you can then use, or as a notebook that allows you to view the code. How do you then use your model? We can deploy it to the Machine Learning service from where it can be called securely by any external code/system!
15. Select the result from the leaderboard that you want to convert to a model, and click the **Save as** button on the right hand side.
16. Select **As a model** then, when that's done, a pop up will appear that allows you to go directly to the model in your project. You can also view the model by going to the **Assets** tab of your project.
17. Your model is just an XML file asset at the moment. In order to turn this into something useful that can run and be called by your code, app, system etc you need to deploy it to the **IBM Machine Learning service**. This service contains run times to allow the model to run when called, and all the security and API management required of a cloud based service. Your model will effectively be available as a secured, cloud based API that can be called however you want, from wherever you want. If you want to deploy your model somewhere else on your own infrastructure you can do that too. Cloud Pak for Data also contains a catalogue feature that allows you to publish your model to your organisation, but that is not covered by this workshop. While viewing the model, click the **Promote to deployment space** button. ![Promote to deployment space](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/promotetodeplymentspace.png)
18. A "Space" is effectively a container to hold your models in. It has controllable access and run time resorces within it. this allows you to manage all aspects of your deployment for a set of models. In the **Promote to space** options page select a space you already have to deloy to (or create a space using the dropdown). Select **Go to the model in the space after deploying it** so you can easily do the next step. ![Promote to deployment space options](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/promotetospaceoptions.png)
19. The next page allows you to create an actual deployment in the space. Click on the **Create deployment** button ![Create deployment](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/createdeployment.png)
20. In the page that appears, select the the deployment method. **Online** in this case. ![Deployment options](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/createadeploymentoptions.png) and provide a name for the deployment.
21. The next page shows the list of deployments you have in the selected space, and their status. After a few seconds your deployment will be "Deployed" which means it is available to be used. Note the three dot menu on the right hand side of the deployment that allows you to **Replace asset** (if you ever update the model) and **Edit configuration** (assign more resources to running it, if it is heavily utilised). ![Deployments view](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/deployments.png)
22. Click on the model to open the page that allows you to test the model with manually entered data and provides the details you need to use the model via Curl, Java, Javascript, Python and Scala. Note that you need the API endpoint credentials (key) to use any of these methods of course. See **Using your model** below on how to obtain this **API key**. Lets test the model! Click on the **Test** tab and enter the 4 sets of data shown below. ![Model testing](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/modeltesting.png)
23. Then click the **Predict** button. You should get these results...
```
{
    "predictions": [
        {
            "fields": [
                "prediction",
                "probability"
            ],
            "values": [
                [
                    "no",
                    [
                        1,
                        0
                    ]
                ],
                [
                    "no",
                    [
                        1,
                        0
                    ]
                ],
                [
                    "yes",
                    [
                        0,
                        1
                    ]
                ],
                [
                    "yes",
                    [
                        0,
                        1
                    ]
                ]
            ]
        }
    ]
}
```
24. As we can see from the result, the 3rd and 4th data sets result in the model predicting failure with a probabilty of 1 ie 100%, as we would expect!

## Using Your Model
In step 21 above we could briefly see how to call the API of our model. That API was created when we deployed our model.
Within Watson Studio our model sits within a deployment. At this point the model is separate from project. That project can be deleted or added to etc with no impact to the deployed model.
Note on the main menu of Watson Studio (click the burger icon at the top left of the Watson Studio page) that there is a section for **Projects** and a separate section for **Deployments** that contains your deployment **Spaces**
To locate your "running" model (essentially get back to the page you see in step 21 above) use the main menu and go to the deployment space that contains your model.
Slightly confusingly the **Space** contains Assets and _**Deployments**_. We have a Deployment/Space/Deployment stucture which seems strange, but that is the way it has been built.
![Deployments](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/deploymentsspacedeployments.png)

Within this **Space** select the **Deployments** tab and click on your model ![Deployments view](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/apireference.png)

This page shows the unique public API endpoint for your deployed model. This endpoint is unique to your deployment and will remain the same if you replace the model with a different one at any time. Note also the sample code provided that can be used to call/use your model from various common languages as well using the basic/universal CURL command. You will note that authentication is required to call the API of course. 

To obatin the API key discussed on this page, click [here](https://cloud.ibm.com/iam/apikeys?_ga=2.107320577.2076131076.1626968412-622637277.1614526710) or go to your IBM Cloud Account and select **Manage** then **Access (IAM)** from the Manage menu on the top menu bar then **API Keys** from the menu on the left of the IAM page that appears. From that page you can create a new API key.

See [here](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html) for more information on the authentication process you'll need to know about before deplying your application.

## Using Your Model with Streaming Data
Now we are ready to apply our model to streaming data.
First we need to authenticate with the ML service. Using the API key you obtained above, run the following command (either substituting $API_KEY for the key or by setting the environment variable API_KEY to the value of the key via whatever process is relevant to your machine's operating system eg

on Mac ```export API_KEY=[your key] ```

Then run tbe following command from a terminal/command prompt
```curl --insecure -X POST --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=$API_KEY" "https://iam.cloud.ibm.com/identity/token"```

JSON data is returned and you will see an access_token value. Copy this value and set the environment variable access_token to this value using the same method as above.

Locate your Space ID and note the location of your service (us-south, eu-gb etc etc). Use both of these to construct your call to the ML service.
You can locate your Space ID by going to Watson Studio and locating the correct space under the Deployments menu then selecting the Manage tab. The Space ID is the Space GUID shown there (as shown below) ![space id location](https://github.com/tim-minter/machine-learning-with-streaming-data/blob/main/spaceID.png)

This is what it would look like for a service located in the UK
```curl --location --request GET 'https://eu-gb.ml.cloud.ibm.com/ml/v4/instances?space_id=[your space id]&version=2020-09-01' -H "Authorization: Bearer $access_token"```

In the USA (Dallas) this would look like this. Check [here](https://cloud.ibm.com/apidocs/machine-learning#endpoint-url) for the correct endpoint for your region 
```curl --location --request GET 'https://us-south.ml.cloud.ibm.com/ml/v4/instances?space_id=[your space id]&version=2020-09-01' -H "Authorization: Bearer $access_token"```

## Next Steps
There are many ways streaming (or flowing or "in motion") data can be analysed with a Machine Learning model.
They range from something like a serverless function monitoring a ftp folder, an API (like the one you created above) being called dircetly by an application, using something like the "low code" NodeRED open source application available on pretty much any playform incliding Raspberry Pi, right up to builing an enterprose AI pipiepline with IBM Data Stage and Apache Kafka (or the IBM managed service version of Kafka... IBM Event Streams) and Watson Studio to manage the whole process end to end.

If you build services or solutions for you cutsomers using IBM technology, IBM can help you with expertise and resources tailored to your situation. Contact xxxx.


