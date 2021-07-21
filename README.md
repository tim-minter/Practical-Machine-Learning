# A Workshop on Practically Applying Machine Learning to Streaming Data using Watson Studio
### You have data streaming in from sensors. You want to train a model on that data and apply it to the data in real time, in the real world

## Introduction
The term "Machine Learning" or "AI" is fairly well understood by a lot of people but when it comes to you actually building a machine learning model and applying it to real data, I, for one had a lot unanswered questions for example:

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

1. Lets create (or can use the file I've made here) some data to train the model with. We'll use data we know will create a model that will give a certain prediction so we can learn how it all works. Essentially the data in this file shows one thing ... once "y deflection" reaches 1.2 we get a failure. Although temperature and x deflection change throughout the file, I've crafted the data so that these should have no baring on the liklihood of failure and we should end up with a model that simply predicts failure as y defelction increases towards 1.2.
2. No we can set up our Data Science environment on IBM Cloud. This is all contained within the [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) service, which you can set up for free (and it will remain available if you use it at least once every 30 days). Create this service and then click the Get Started button.
3. Slightliy confusingly, this then opens "IBM Cloud Pak for Data" but don't worry, Watson Studio is integral to Cloud Pak for Data so this is what Watson Studio runs within.
4. Underneath the welcome message you'll see three options. Select *Create a project* link under *Work with data* then click *Create and empty project*
5. Give the project a name. Every project will have files and data associated with it and they need to be stored somewhere. You may be asked to create some Cloud Object Sorage at this point. If you are, then follow that process then click Create to create the project. If you already have storage configured this will automatically be selected.
6. You'll then be presented with a page where you can add and manage all the components of the project. One this to note here is the Environments page. This is important to track how much of your free credit is left, and if you sign up for the paid service, how much resource it is using.
7. 

## Next Steps
