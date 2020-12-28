# First Party Fraud Monthly Business Report


## Report Context
Monitoring and Reporting is a vital component of making data-based decisions as you can look at higher level or earlier metrics to understand the impact of a given policy. The Monthly Business Report is usually an analyst's first responsibility at Capital One, in compiling the report analysts gain expertise in the data sources and filters they will need to do their job, as well as an understanding of what metrics are important to the team.

The unfortunate reality is, reporting and monitoring can take a **long** time, especially if the data deviate from what was expected, and even more so if performance starts to worsen. Leadership will want to understand **why** performance is moving in the direction it's going. Spending days creating data tables, pulling the numbers, and then making graphs -- only to have to repeat this process to understand why performance is changing can take weeks, which is problematic as analysts have to do this every month.

This was exactly the situation I found myself in as I rotated onto the First Party Fraud team in August 2019. In my first month, I was in charge of presenting the Monthly Business Report. I had been given inheritance documentation and scripts of the past process the previous analyst used, with the process taking approximately one week to produce a standarized set of slides.

Capital One has been investing heavily in automation and its data platforms and processes, and released an internally built python package that automates the creation of slide for analysts.

Using this package, I set out to automate the monthly business report in my first month, so that I could save myself weeks of time going forward when creating the report. 

## Report Workflow

The steps required to create the report, at a high level are:

    1. Run SQL queries to create data tables with up-to-date data on KPI, starting with account level granualrity
    2. Aggregate the data into monthly performance
    3. Create Graphs that visualize the data over time
    4. Format the graphs to comply with Capital One standards -- these reports are highly scrutinzed and go to regulators such as the OCC
    5. Describe what is important in the slide, how has performance changed, is there something to takeaway from the visualization?
    6. (Optional) Explain why KPI moved in the last month
    
The sixth step is optional, as usually an analyst is juggling multiple responsibilities simultaneously and might not have time to dive deeper into why performance changed the way it did.

## Repository Structure

Mimicking the Report workflow, the repository follows a similar process:

    1. Data Creation Scripts
    2. Graph Creation Scripts
    3. Trigger Script
    
To complete the first task of having up-to-date data, I created scripts that run on a weekly automated cadence. The scripts pull KPI, so that each Friday, we have the latest de-aggregated data automatically. If there are errors in this process on a given week, analysts will know before they attepmt to create the report giving them precious debugging time. 

The second through fourth tasks, the meat of the report are done primarily through the Graph Creation Scripts. These scripts pull from the data sources created from the Data Creation Scripts, aggregating them at a monthly level, and formatting them for the visualizations used in the report. The formatting is aided by the **Trigger Script.**

The Trigger Script is a singular iPython notebook that runs each of the Graph Creation Scripts, compiling the views created by these scripts into one powerpoint slide. The Script then emails out **50** powerpoint slides that visualize how various KPI have moved.

Unfortunately, there's no way to automate the Slide Description or deep dives, as analysts must use their judgement to call out the main points of a visualization. However, by running one script and having automated processes aid with the data creation, analysts can complete 80% of the powerpoint letting code compile, while working on other activities -- a massive increase in productivity.

## Navigating this repository

To get the best understanding of this process, I would recommend the audience start at the Data Creation Folder, then move-onto the graph creation folder and finally the trigger script itself.

## Strengths of the infrastructure


### Collaboration
This repository has helped promote collaboration on the Monthly Business Report, as any analyst can modify the existing code if they encounter errors or need to make changes to the underlying scripts as data sources change.

### Scalable
Additionally, if new views are required, thanks to the trigger scipt, all you need to do is create a new script in the graph creation folder and add one line of code to the trigger script. This greatly simplifies and reduces clutter.

### Modular 

The most useful aspect of the trigger script framework is the **unit test** parameter. When running scripts from the trigger script, you can pass parameters that will influence the way a script is run. 

Running the entire trigger script takes 3+ hours for the 50 slide output. If one section is erroneous it would be extremely painful to spend 3 hours to see whether or not changes made actually debugged the issue. To facilitate a faster debugging process, the unit test parameter was created. If an analyst sets unit test to 'yes', that particular script will email out the slides it created. This means that analysts can debug any one part of the chain without having to mess with the infrastructure or underlying graph creation scripts.
