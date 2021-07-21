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

## Next Steps
