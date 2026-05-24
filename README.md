# Machine-Learning
This repo will showcase my journey in Machine Learning. 
## To-Do List Reality Check
### Overview
To-Do List Reality Check is a machine learning model that will predict the possibility of a task being finished or not. Personally, I have been very much inclined to multitasking and learning a variety of subjects and topics simultaeneously. Not only that, but also take pleasure in writing unrealistic tasks while at the end of the day, I ended up finishing none of the tasks that I have set.

And thus, To-Do List Reality Check was born, a ML model that will give me a prediction of whether a task is viable or not.

One-line description: A Reality Check to humble for those who have been delusional with their Absurdity on their potency for the to-do lists ☺️

### Approach
Starting with a base model from Hugging Face: DistilBert(uncased) model.

### Feature Extraction
Firstly, I will use Feature Extraction for this pre-trained model. Freezing the DistilBert's weights, I will take the embeddings from the frozen layers fromt the model and then train a new Linear layer and then use Sigmoid to produce a prediction of either "Possible" or "Not Possible".

### Data Input -> Frozen weights -> embeddings -> Linear Regression -> Possible/Not Possible

### Dataset
For the dataset for the model to train on, the features will be as following:

Subject (ML, Math, CSC105, GEN)
Difficulty level (Easy, Medium, Hard)
Time taken (30 mins, 1 hr, 3 hrs, 5 hrs)
Date (Todo lists will fall on the same date)
The model will predict the tasks from the same date. And among the todo-list tasks from that day, it will predict whether to shorten the tasks or not by providing prediction for each individual task as 'Possible' or 'Not Possible'.

The dataset will hold ~500 rows.

### Manual Data Production with Claude Code
Since there's no sufficient record of my past todo lists, I have Claude Code to produce makeshift datasets based on the features of the ones mentioned above.

### Predicting against my study time
The dataset was produced by prompting Claude to generate data that aligns with the self-study time I have each day: 5 hours.

Easy tasks take 30 minutes or 1 hour, Medium tasks take 3 hours, and Hard tasks take 5 hours. If there is one Easy task and one Hard task on the same date, the model should predict "Not Possible" since the total exceeds 5 hours. However, if there is only one Hard task in a day, it should predict "Possible."

Of course, this problem could simply be solved programmatically by summing up the total hours of all tasks on the same date and checking whether it exceeds 5 hours. Nevertheless, since this is an ML project, the point is to build a model that learns the pattern on its own: predicting "Possible" when the total time doesn't exceed 5 hours and "Not Possible" when it does.
