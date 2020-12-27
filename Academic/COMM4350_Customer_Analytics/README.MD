COMM 4350 - Customer Analytics and Brand Strategy was class I took spring 2018, my last semester as a part of the McIntire School of Commerce at UVa. Like other School of Commerce courses, the course sponsored with an industry partner - E&J Gallo. The goal of the project was extremely open-ended, propose a new alcoholic beverage that E&J Gallo should introduce in under $15 segment.

The course material, which covered:
    
    1. Brand Equity
    2. ZMET analysis
    3. Social Analytics
    4. Text Analytics
    5. Multi-Variate analysis technics

and the [UserTesting tool](https://www.usertesting.com/) for customer experience research helped guide the class's approach through the semester. 

This portfolio contains the two final deliverables, a presentation presented to E&J Gallo Brand Representatives, and the proposed product brand charter. 

To facilitate student's completion of the project, E&J Gallo shared survey data they had on customer's perceptions of various brands and products in the alcoholic beverage industry.

This class was a blast! I'm happy to say it was my first A+ at the University of Virginia, and I believe that my success was driven by the merging of my statistics background and polished business insight and continued collaboration with teammates I wokred with in the past.

As a member of the team, my contributions included:

    1. Sanitizing and cleaning the raw survey data so analysis would be possible in R/ggplot2 
    2. Performing competitive analysis on the under $15 alcoholic beverage industry, utilizing Ggplot2 to visualize the space
    3. Conducting K-NN to determine the number of unique brand profiles, and find a white-space in the market
    4. Build a Random Forest model in R to label a prospect into one of the customer persona
    5. Performing a Principle Components Analysis on the Survey variables to maximize informatoin gained
    6. Sensitivity analysis on Revenue expectations of the proposed brand charter
    
# Data Sanitization and Cleaning

The survey data given by E&J Gallo came in a manner I was prepared for -- dirty, not formatted and filled with plenty of NA's (see slide 32 of the presentation). To get from a mess of a csv to the long data format required for ggplot2, I leaned heavily on the tidyverse set of librarys in R utilizing Hadley Wickham's [R For Data Science](https://r4ds.had.co.nz/). After setting values_drop_na = TRUE in the pivot_longer function, I was able to get to a starting point for futher analysis. 

# Competitive Analysis

In pages 4-11 of the report, I broke down the $15 segment and highlighted where the industry was heading using clever visualizations in ggplot2 and Tableau. First, I looked at the overall-growth rate of the various wine segments, expanding beyond the $15 range; it was clear that premium priced beverages were growing, while the popular segment (defined as $15 and under) remained flat. Customers were willing to spend more to feel more premium. 

The next part of the analysis was to make sure any new brands proposed, did not cannibalize sales of existing E&J Gallo Product, I mapped the industry by percentage of revenue attributable to a particular brand. E&J Gallo was primarily concentrated in the Barefoot brand, introducing a brand that aimed to meet the same customer needs would not drive growth for E&J Gallo. The last part of analysis involved looking at which product-lines were growing the fastest in 2016. On page 7, a Tableau Treemap highlighted that La Marca (Prosecco) and Andre (champagne) were the fastest growing brands in the industry.

From there we had our project direction -- a brand that wouldn't cannabilize Barefoot in the popular segment that still tapped into the premium fervor that was gripping America. Our team's brand propsal, Ice Horse a dessert ice wine played to the heritage of E&J Gallo and a resurgence in wine-cocktail beverages based off these insights.


# K-NN Analysis

Faced with the research questions: Are there any potential consumer segments that would align well with the branded ice wine? What factors are most important for these consumers? I set out to understand the profiles of existing Brands using E&J Gallo's Data. I ran a clustering analysis on customer demographic attributes and brand values, producing a scree plot, found on page 40 of the report. This shows that there were 4 meaningfully distinct customer profiles that shopped for wine-cocktails and wine brands marketing as wine-cocktails, highlighted on slide 20 of the presentation. 

From there, it was important to understand which segment was most valuable to E&J Gallo. On slide 21, I found that _Enthusiastic Emmas_ scored most favorably on two features we would associate with ice wine drinkers -- _Good Host_ and _Mixability_w/Juice_. 

# Random Forest Model

I wanted to further test our hypothesis that this segment was actionable and identifiable. Using a training set and testing set, I built a randomForest model in R to predict a prospect's customer profile as one of 4 members, visualized on slide 49 of the presentation through the rattle R package. Ultimately, the model had a 92% test accuracy on Enthusiastic Emma's signalling there was promise to build a marketing campaign focusing on this profile. 

# PCA Analysis

The highlight of the project for me was submitting a genuine recommendation the E&J Gallo would follow surrounding it's data collection practices. After the cleaning process, intial exploratory analysis showed how the data were not perfect. Pages 48-56 detail this process. Initial multi-collinearity plots showed the attributes were highly correlated with each-other. Ultimatley this meant that E&J was gaining little unique information from some of the questions they were asking. To find out which attributes captured the majority of unique customer attitudes I ran PCA on the dataset. The analysis found that the survey's 24 semantic questions could ultimately be reduced to 12.  Slide 33 covers which of those variables were actually important in the survey. When presenting this analysis to Lee Susen of E&J Gallo, he was stunned by the results and mentioned that he would note this analysis back to the company.

# Sensitivity Analysis and Monte Carlo Simulations

Lastly, after proposing a brand charter, our team was tasked with proposing the market potential for this idea. Highlighted on page 48 of the report, was our team's assumptions used to calculate potential revenue. On page 78, we ran 10,000 simulations using a set of bear and bull conditions to find the 95% confidence interval of potential revenue.
