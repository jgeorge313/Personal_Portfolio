# FPF


## What is First Party Fraud?

First party fraud is defined as: Credit fraud in which a customer of a bank uses his or her own name and information to obtain high-value loans with no intention of paying them back. Also known as credit muling.[Source](https://www.creditcards.com/credit-card-news/glossary/term-first-party-fraud.php)

## Purpose of this repository
This repository outlines the framework i used to create a modular, and scalable infrastructure that automates monthly reporting used for the First Party Fraud'S Monthly Business Report.

This is a routine, but business critical output that gets sent to regulators such as the OCC monthly. The primary purpose of this monitoring is to understand emergent fraud trends, and measure performance of new defenses.

Before I joined the team, the report took a week to compile, as the analyst had to:

1. manually run the SQL that would create the underlying views necessary for the graphs in the deliverable
2. Run the select queries on those tables
3. Create the graphs using the data above
4. Format the slides in the report
5. Analyze and Interpret the month's performance
6. Deliver the presentation
As a fan of automation and the power of Python I have increased the quality of the presentation, while reducing the time necessary to compile it.

Using an automated scheduler I:

    1. Create a sequence of jobs which run every Friday at 5 am. These jobs create the tables used in monthly reporting, with the latest data.
    2. Run a master script. This script installs all necessary packages, creates all relevant variables, including the powerpoint object and then
    runs a series of scripts.
        A. Each script selects the data necessary for the graphs in the deliverable. The script, utilizing a Capital One built python package, takes those
    dataframes and creates automatically formatted powerpoint charts. 
        B. After running, each script, the script exports a powerpoint file of 52 slides, each already formatted

Additionally, since the master script is a modular framework - the team has expanded monitoring greatly from the 24 views we used to look at, as the team can continue to add new views and have them be output automatically without needing to do any of the manual work.

I have created new views that examine specific deaggregated data, that are useful to identify drivers of emerging fraud trends, such as losses by geography or the line of business.

Ultimately this work has improved consistency, reduced the completion time, and expanded the scope of the Monthly Business Report.

This repository will mock the script repository used to create the outputted powerpoint file.

