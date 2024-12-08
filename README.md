## Predicting Abandonment for Open-Source Projects on Github

The primary objective of this project is to answer the key research question: What features of open-source projects are good indicators of the projects’ abandonment, and how can these features be used to predict and measure the likelihood of abandonment? In answering this question, we seek to…

- Identify and define the key features of open-source software projects that can predict open-source abandonment
- Build a model to predict the likelihood of an open-source project being abandoned
- Create a metric to measure the risk of open-source abandonment

#### [Link to our documentation for the data scraping tool](https://docs.google.com/document/d/1Jjpl1xQaMB6FtYWBYjZK0QVgoFTovrYyPYvRcOOTF3k/edit?usp=sharing)


### Data Scraping Automator

Data is automatically scraped every Sunday night/Monday morning at midnight using Git Actions. The data goes straight into the features folder, but to explore what's going on, you can check it out in the Actions tab. To edit the workflow, you would want to edit **.github/workflows/github-actions-demo.yml**.

**If you are participating in this research project: You will need to create a new SSH key on your own GitHub account, as the current one is set to expire on March 2nd, 2025. To do this, you can follow the SSH section of the data scraping tool documentation linked above. Then, when you have the SSH key, you need to go to the settings of this repository, and under Secrets and Variables, select Actions, then edit the Repository Secret called SSH_PRIVATE_KEY.**

You may notice that every week, over 10 different excel sheets are added to the features folder from the data scraping automator. The sample being scraped is split into multiple smaller samples due to Git Actions having a 6 hour limit on each job, so each smaller sample is a separate job in a workflow. You could hypothetically have up to 20 jobs running concurrently, but beyond that they would start being queued up. 

#### Issues with the Automator
If an issue occurs with the automator, my assumption is that it would be one of three things: the SSH key has expired, a dependency is outdated, or a job timed out. You can view the error message provided in Git Actions by clicking on the failed workflow and address what the error was. If the problem was a job hitting the 6 hour limit, you can either rerun the job, or if it is a recurring problem, you may need to split the sample into two pieces and add a new job for the next part of the sample.

### File Organization

We've already covered the contents of .github/workflows and features.
Under models, you will find the colab notebooks with various models and tests, and descriptions. The more currently relevent one is Git_Models.

Under src, there are a number of folders. Most of them went unused for me, but I didn't want to delete anything in case I missed something important. If you fork this repository, feel free to clean it up. The only one that you will probably need is src/main. In here, you can find the samples folder that contains the samples that the automator uses. src/main also contains the python scripts that the automator uses: api_modified.py, clone_scraper.py, etc.




