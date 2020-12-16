The Business Analytics class was a class I took during my Fall Semester at the McIntire School of Commerce at the University of Virginia. The class partnered with a real company, ApartmentGuide.com. The class covered many data science concepts and algorithms, , including k-NN clustering, boosted and bagged models, cross validation using the RapidMiner software. The primary deliverable of the class was the semester long project using real data from ApartmentGuide.com to provide a business recommendation for the company. 

Our team developed a model that predicted whether a consumer would revisit given an ad, and then from there knowing that return visits
are more likely to digitally convert, estimated the marginal value this project would bring to the company. 

This project and presentation were well received, with the Professor using it as the exemplar presentation in the following semester's class of Business Analytics.


As the statistics major in the group, there were many parts of the project I was **heavily** involved with:

* [Lead Model Building process](https://docs.google.com/spreadsheets/d/1cTd5uGjXgF_-3J6KWbRs3bOccydrGfTOt1jeKCiscrw/edit?usp=sharing)
* Translating the model into actionable and communicable business value
* [Lead model cross validation process and taught best practices to teammates](https://docs.google.com/spreadsheets/d/1cTd5uGjXgF_-3J6KWbRs3bOccydrGfTOt1jeKCiscrw/edit#gid=1318390983)
* Estimating the financial value of this business analytics project
* Using Monte-Carlo Simulation to provide a confidence interval of our project's business value
* Performed K-NN clustering to find 4 marketable and sizeable segments using the digital analytics data 

    
  
 Delving into each of these processes a little bit more:
  
  ### Model Building Process
  
This class went over how to create predictive models and almost all of the cutting-edge algorithms that businesses use to for their analytics problems. For this class, there were two priorities: a high class 0 recall<sup>1</sup> and also an explainable model. Therefore our team started off with competing interests - choosing less complex models that were understandable (i.e. regression) versus more complex models (i.e. Neural Nets). Not only that, our team was hard capped by time, meaning models that took longer to run limited our opportunity to iterate. I addressed this problem early on by testing various different algorithms of differing complexities (SVM, stacked models, logistic regression, K-NN, random forests, and boosted-decision stumps). Given the high run time and low explainability of Neural Networks our team did not run those models until we had two sufficient models to select from. We found that the advanced model running only on 3 features was just as competitive as our winning model a boosted decision stump trained on 53 features. 


### Translating the model into actionable and communicable business values

As mentioned before, since our team was tasked up front with explaining how our model would actually make an impact for the company, we decided to discard the Neural Net from our top 3 models, and were left with a boosted decision stump and a k-NN clustering where K = 53.
There were two reasons we chose the boosted decision stump - the first and primary reason was that the model had a lower variance; the k-NN was highly erratic depending on the sample data as we found when running cross validation. Secondly, the boosted decision stump, while complex sounding can be logically explained as an "advanced decision tree model" which is simply a model that looks at key features in the data and uses it to predict whether a consumer will revisit if served an ad. In fact, it allowed our team to explain why our model worked = as feature importance showed that device type was instrumental into predicting successful leads.

### Lead model cross-validation process and taught best practices to teammates

This section was driven by my understanding of the bias-variance tradeoff, a fundamental principle in machine learning and data science. 
It's extremely important to be accurate, regardless of the data presented, a model such as the k-NN, doesn't have any deep logic behind it, and is extremely sensitive to the data sample it is validated on. When deciding which model to ultimately use, I convinced the team to choose the Boosted Decision Tree, primarily for this reason. Additionally, this helps our project have a more stable financial projection for our project.

### Estimating the financial value of the business project

I presented slide 12 to the CEO of the company, where I explained at a high level the general process of our projection - because the rationale of any financial projection should be given up-front to business leaders, so they, with their more intimate knowledge of the market, can see where there could be some key risks. Additionally, this projection, was complex - we were looking at the incremental value of this marketing campaign, as naturally conversions occurring could not be included in the projection. This is why I elaborated on this single slide with 8 appendix slides, which came in handy when the CEO had a question on the specifics of this projection.

### Using Monte-Carlo simulations to provide a confidence interval on the project's business value

After our group had used our model to predict our financial projection, it was inherently important to communicate the sensitivity of our model. While a cross validation accuracy would serve well in a mathematics course, I knew a business leader would want that context 
in dollars. That's why I ran 1,000 Monte-Carlo Simulations of our model, for the excel file, see the "
Monte Carlo Projections" excel file. 



### Performed K-NN clustering to find 4 marketable segments using the digital analytics data

The important aspect of this segmentation from the group's perspective was that the clusters be relatively distinct, and relatively sizeable. Given this, we immediately noticed that the device feature was clearly segmentable, as Android users converted more. In the Q&A, the CEO specifically asked why we thought Android users converted more and informed us that it's because Android browsers could call directly from the phone. 




<sup>1</sup>: High class 0 recall instead of overall accuracy was the chosen model parameter to optimize on as the cost of serving an ad to a consumer to who doesn't convert is much lower relative to the financial gain of a converting retargeted visit.
